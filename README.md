import socket

target = input("Enter target IP or website: ")

print("Scanning target:", target)
print("Please wait...")

ports = [21,22,23,25,53,80,110,139,143,443,445,8080]

for port in ports:
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    socket.setdefaulttimeout(1)
    result = s.connect_ex((target, port))
    
    if result == 0:
        print("Port", port, "is OPEN")
    else:
        print("Port", port, "is CLOSED")
    
    s.close()

print("Scanning completed.")
