# morse-code-converter
# morse_code.py

MORSE_CODE_DICT = {
    'A': '.-', 'B': '-...', 'C': '-.-.', 'D': '-..', 'E': '.', 'F': '..-.',
    'G': '--.', 'H': '....', 'I': '..', 'J': '.---', 'K': '-.-', 'L': '.-..',
    'M': '--', 'N': '-.', 'O': '---', 'P': '.--.', 'Q': '--.-', 'R': '.-.',
    'S': '...', 'T': '-', 'U': '..-', 'V': '...-', 'W': '.--', 'X': '-..-',
    'Y': '-.--', 'Z': '--..',
    '1': '.----', '2': '..---', '3': '...--', '4': '....-', '5': '.....',
    '6': '-....', '7': '--...', '8': '---..', '9': '----.', '0': '-----',
    ', ': '--..--', '.': '.-.-.-', '?': '..--..', '/': '-..-.', '-': '-....-',
    '(': '-.--.', ')': '-.--.-', ' ': '/'
}

def text_to_morse(text):
    return ' '.join(MORSE_CODE_DICT.get(char.upper(), '') for char in text)

def morse_to_text(morse):
    reverse_dict = {v: k for k, v in MORSE_CODE_DICT.items()}
    return ''.join(reverse_dict.get(char, '') for char in morse.split())

if __name__ == "__main__":
    import argparse

    parser = argparse.ArgumentParser(description="Convert text to Morse code and back.")
    parser.add_argument("mode", choices=["encode", "decode"], help="Mode: encode (text to Morse) or decode (Morse to text)")
    parser.add_argument("message", help="The message to encode or decode")

    args = parser.parse_args()

    if args.mode == "encode":
        print(text_to_morse(args.message))
    else:
        print(morse_to_text(args.message))
