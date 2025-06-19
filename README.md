<h2 align=center>How to Connect to GPU via SSH</h2>

- First open, command prompt (cmd)
  - Method 1 : To open command prompt, press `Windows` and `R` key together and then write `cmd` there and then press `Enter` button
  - Method 2 : Write `cmd` in the searchbar (located on the taskbar below) and then click on `open` button to open command prompt
    
  ![Screenshot 2025-06-19 142832](https://github.com/user-attachments/assets/55b6f4ca-000b-479e-bbdc-1b9c2026d35b)

- Run the following command in Command Prompt to generate an RSA key pair :
  ```
  ssh-keygen -t rsa -b 4096 -C "gpu" -N "" -f "%USERPROFILE%\.ssh\id_rsa"
  ```
- If a key already exists, this will prompt something like this
  
  ![Screenshot 2025-06-19 143543](https://github.com/user-attachments/assets/eecb6381-a29f-4d8f-a800-61e1d346fd17)

  In this case, write `y` to overwrite.

- Then, use the below command to view the public key :
  ```
  type "%USERPROFILE%\.ssh\id_rsa.pub"
  ```
- Copy the displayed public key, then go to the website of the GPU provider from which you rented your GPU.
- On the provider’s website, look for SSH Key option, it's usually found under Settings or Security. Paste the copied public key there and save the changes.
- Now Copy the SSH command provided by your GPU provider. Open Command Prompt again and paste the command. Press Enter to connect to your GPU server via SSH

<h2 align=center>Some FAQs</h2>

- **Can I use Windows PowerShell or a Linux VPS instead of Command Prompt?**
  - No, you should not do that. The above commands are specifically written for Windows Command Prompt. Using PowerShell or a Linux VPS would require different commands.

- **How do I know if I'm on the GPU server or still in the Windows environment in Command Prompt?**
  - If you're in the Windows environment, your prompt will look like this :
    
    ```
    C:\Users\YourName>
    ```
  - But if you're connected to the GPU server, you'll see something like:
    
    ```
    ubuntu@server-name:~$
    ```
    ```
    root@gpu-instance:~$
    ```
- **If I have already connected to the GPU via SSH key and then close Command Prompt, will I need to reconnect later?**
   - Yes, exactly. You’ll need to copy the SSH command provided by your GPU provider and paste it into Command Prompt again to reconnect.
