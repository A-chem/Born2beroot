
**UFW (Uncomplicated Firewall)** is a tool used to manage your computer’s firewall. A firewall helps protect your computer from unwanted or dangerous network traffic by controlling which connections are allowed and which are blocked.

### Key Points:

1. **What is a firewall?** A firewall acts like a barrier between your computer and the internet. It lets in safe traffic (like web pages) and blocks harmful traffic (like hackers trying to access your system).
    
2. **Why use UFW?**
    
    - **Easy to use**: UFW makes setting up the firewall simple. You don’t need to know complicated commands.
    - **Protection**: It helps keep your computer safe by controlling which services or programs can communicate with the outside world.
3. **Common UFW Commands**:
    
    - `sudo ufw enable`: Turns on the firewall.
    - `sudo ufw allow <port>`: Allows traffic on a specific port (like port 80 for websites).
    - `sudo ufw deny <port>`: Blocks traffic on a specific port.
    - `sudo ufw status`: Shows which ports are open or closed.

### Example:

- If you want to allow SSH access (for remote login), you would run
    
    `sudo ufw allow 22`
    
    This allows people to connect to your system using SSH.