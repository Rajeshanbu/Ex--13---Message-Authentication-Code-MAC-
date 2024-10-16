# Ex--13---Message-Authentication-Code(MAC):
## AIM:
To implement a simple MAC using XOR for verifying message authenticity.

## ALGORITHM:

### STEP 1:
Input a secret key and the message to be authenticated.

### STEP 2:
Use a basic XOR operation between the key and the message, repeating the key as necessary to match the length of the message.

### STEP 4:
Display the generated MAC in hexadecimal format.

### STEP 5:
Input a received MAC and compare it with the computed MAC for verification.

## PROGRAM:
```py
# Define MAC size in bytes
MAC_SIZE = 32

# Function to compute a simple MAC using XOR
def compute_mac(key, message):
    key_len = len(key)
    msg_len = len(message)
    
    # Initialize the MAC as an empty bytearray
    mac = bytearray(MAC_SIZE)
    
    # XOR the key and message, repeating if necessary
    for i in range(MAC_SIZE):
        mac[i] = ord(key[i % key_len]) ^ ord(message[i % msg_len])  # Simple XOR operation
    
    return mac

def main():
    # Step 1: Input secret key
    key = input("Enter the secret key: ")

    # Step 2: Input the message
    message = input("Enter the message: ")

    # Step 3: Compute the MAC
    mac = compute_mac(key, message)

    # Step 4: Display the computed MAC in hexadecimal
    print("Computed MAC (in hex): ", end="")
    for byte in mac:
        print(f"{byte:02x}", end="")
    print()

    # Step 5: Input the received MAC (for verification)
    received_mac_hex = input("Enter the received MAC (as hex): ")
    received_mac = bytearray.fromhex(received_mac_hex)

    # Compare the computed MAC with the received MAC
    if mac == received_mac:
        print("MAC verification successful. Message is authentic.")
    else:
        print("MAC verification failed. Message is not authentic.")

if __name__ == "__main__":
    main()

```
## Output:
![image](https://github.com/user-attachments/assets/a66d3801-1c19-4c70-a38e-5dce9265f45e)
## Result:
The program for generating and verifying a simple Message Authentication Code (MAC) using XOR was successfully implemented and executed. The computed MAC helps ensure the authenticity of the message by verifying its integrity.


