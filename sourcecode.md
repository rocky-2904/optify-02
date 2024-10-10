    # Caesar Cipher Encryption and Decryption
    def caesar_cipher(message, key, mode='encrypt'):
    result = ''
    key = int(key) % 26  # Key should wrap around in case it's larger than 26
    
    if mode == 'decrypt':
        key = -key

    for char in message:
        if char.isalpha():
            shift = 65 if char.isupper() else 97  # Differentiating between upper and lower case
            result += chr((ord(char) - shift + key) % 26 + shift)
        else:
            result += char  # Non-alphabet characters remain the same

    return result


    # Vigenère Cipher Encryption and Decryption
    def vigenere_cipher(message, key, mode='encrypt'):
    result = ''
    key = key.lower()  # Ensuring the key is in lowercase
    key_length = len(key)
    key_index = 0
    
    for char in message:
        if char.isalpha():
            shift = ord(key[key_index % key_length]) - 97  # Get shift from the key
            
            if mode == 'decrypt':
                shift = -shift  # Reverse shift for decryption

            base = 65 if char.isupper() else 97
            result += chr((ord(char) - base + shift) % 26 + base)

            key_index += 1  # Move to the next key character
        else:
            result += char  # Non-alphabet characters remain the same
    
    return result


    # Main program
    def main():
    print("Choose Cipher Type: ")
    print("1. Caesar Cipher")
    print("2. Vigenère Cipher")
    
    choice = input("Enter choice (1 or 2): ")
    
    message = input("Enter the message: ")
    key = input("Enter the key (for Caesar, use a number; for Vigenère, use a word): ")
    mode = input("Choose mode: 'encrypt' or 'decrypt': ").lower()

    if choice == '1':
        result = caesar_cipher(message, key, mode)
    elif choice == '2':
        result = vigenere_cipher(message, key, mode)
    else:
        print("Invalid choice!")
        return

    print(f"Result: {result}")

    #Run the program
    if __name__ == "__main__":
      main()
