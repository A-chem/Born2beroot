
TTY ( **Teletypewriter**) refers to a terminal or command-line interface session. In the context of `sudo` and system security, **TTY mode ensures that `sudo` commands can only be executed from an interactive terminal**.

This setting prevents certain automated or non-interactive methods of using `sudo`, which enhances security by requiring direct user interaction.

---

### **Why Enable TTY Mode for sudo?**

1. **Prevent Automated Attacks**: Without a TTY, attackers could use scripts or malicious processes to escalate privileges without requiring user interaction.
2. **Enhance Accountability**: Ensuring commands are run interactively makes it easier to track user actions.
3. **Improve Security**: It blocks certain non-interactive shells or remote executions that bypass TTY requirements.

---

### **How to Enable TTY Mode in sudo?**

You need to modify the **sudoers file** to require TTY mode for all users.

#### Step-by-Step Instructions:

1. Open the `sudoers` file safely using the `visudo` command:
    
    `sudo visudo`
    
2. Add the following line (or uncomment it if already present):

    `Defaults requiretty`
    
    - This enforces TTY mode, meaning `sudo` commands can only be run from an interactive terminal.
3. Save and exit the file.