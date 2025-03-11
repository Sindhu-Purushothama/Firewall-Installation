**Introduction**

Firewalls are essential components in network security that act as barriers between trusted internal networks and untrusted external networks. 

They filter traffic based on security rules to prevent unauthorized access and protect systems from potential threats. Properly configuring and testing firewall rules ensures that only legitimate traffic is allowed while malicious or unauthorized attempts are blocked.

**What is the name of the default firewall on your OS?**

Default Firewall on OS

- **Windows**: Windows Defender Firewall
- **Mac**: macOS Firewall
- **Linux**: iptables or firewalld (depending on the distribution)

On Windows, the name of the default firewall is "Windows Defender Firewall." To check this on your system, you can follow these steps:

### Method 1: Using Windows Settings

1. **Open Settings**: Press `Win + I` to open the Settings app.
2. **Go to Update & Security**: Click on "Update & Security."
3. **Navigate to Windows Security**: In the left-hand menu, click on "Windows Security."
4. **Open Firewall & Network Protection**: Click on "Firewall & network protection" to see the status of the Windows Defender Firewall.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/4ab93c48-ac2a-434d-bb1c-e6bc7bac5137/Untitled.png)

# **Creating a Firewall Rule to Block the Google Server (8.8.8.8)**

### On Windows:

1. **Access Windows Defender Firewall**:
    - Open **Control Panel**.
    - Navigate to **System and Security** > **Windows Defender Firewall**.
    - Click on **Advanced settings**.
2. **Create a New Outbound Rule**:
    - In the **Advanced Security** window, click **Outbound Rules** on the left.
    - Click **New Rule** on the right.
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/ea1b2e3c-6840-4591-a196-80defb100702/Untitled.png)
    
    - Choose **Custom** and click **Next**.
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/2a96e104-98e4-4325-9265-67073ecc76f4/Untitled.png)
    
    - Select All **program** and click **Next**.
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/fc52d776-52a0-4590-b7c9-6118feda3abb/Untitled.png)
    
    - Leave the default `Any` for Protocol type and click `Next`.
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/f7568152-c881-4810-a2a1-9256e3da912f/Untitled.png)
    
    - On **Which remote IP addresses does this rule apply to?**, select **These IP addresses**, and enter `8.8.8.8`. Click **Next**.
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/f1fe65c8-1f99-4232-91b2-5cc33644affb/Untitled.png)
    
    - Choose **Block the connection** and click **Next**.
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/f8997abb-63b6-480d-a991-0424f7ce96d0/Untitled.png)
    
    - Select the profile (Domain, Private, Public) and click **Next**.
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/665b35c4-d44d-4279-bb2f-b7e6eb7ec1c6/Untitled.png)
    
    - Name the rule (e.g., Block Google DNS) and click **Finish**.
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/10cf5f0c-01e9-4485-ba2d-185f325db279/Untitled.png)
    

Once after you click finish,The rule could be seen as below.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/e2329542-7929-4bd8-9ca8-2958d5bff232/Untitled.png)

# Testing Connectivity

1. **Visit Google Homepage**:
    - Open your web browser and try to access `www.google.com`.
    - You should see an error page indicating that the site cannot be reached.
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/3b4612ae-2494-4427-be8b-50ea5e3f91dc/Untitled.png)
    
2. **Ping the IP Address**:
    - Open the command prompt (Windows) or terminal (Mac/Linux).
    - Run `ping 8.8.8.8`.
    - The result should show "Request timed out" or similar messages indicating that the pings are blocked.
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/42ab873f-9e41-4d37-bb9c-0c6b5c088879/Untitled.png)
    

### Finding Firewall Logs

- **Windows**: Firewall logs are located in `C:\Windows\System32\LogFiles\Firewall\pfirewall.log`

### Steps to Access Windows Firewall Logs

1. **Open Windows Defender Firewall with Advanced Security**:
    - Press `Win + R`, type `wf.msc`, and press `Enter`.
2. **View Firewall Properties**:
    - In the left-hand pane, click on `Windows Defender Firewall with Advanced Security on Local Computer`.
    - In the middle pane, click on `Windows Defender Firewall Properties`.
3. **Configure Logging**:
    - In the Windows Defender Firewall Properties window, click on the `Private Profile`, `Public Profile`, or `Domain Profile` tab (depending on which profile you want to configure logging for).
    - Click on the `Customize` button under the "Logging" section.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/18cca2cc-5ce4-4952-8c10-f5dbe721ce4b/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/fccd722a-9442-43d8-8a74-1310057fb52f/Untitled.png)

**Enable Logging**:

- In the Customize Logging Settings window, make sure "Log dropped packets" and "Log successful connections" are set to `Yes`. Make sure these settings are enabled in the below three highlighted tabs(Domain profile,private profile and public profile ).

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/dd729cca-0fa3-48fa-bc50-d003a83952ba/Untitled.png)

- Take note of the "Log file path" to know where the logs are being saved. By default, it is: `%systemroot%\system32\LogFiles\Firewall\pfirewall.log`.

**View the Logs**:

- Navigate to the log file path (e.g., `C:\Windows\System32\LogFiles\Firewall\pfirewall.log`).
- Open the `pfirewall.log` file using a text editor like Notepad.

### Screenshot of Firewall Logs

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/4e6a2705-78f7-4c6c-97f5-8054b2b2c6ba/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/acc00667-2360-49fb-965b-a834a6ccdd62/Untitled.png)

### Disabling the Firewall Rule

1. **On Windows**:
    - Go to **Control Panel** > **System and Security** > **Windows Defender Firewall** > **Advanced settings**.
    - Select **Outbound Rules**.
    - Find the rule you created (e.g., Block Google DNS), right-click, and select **Disable Rule** and after disabling the setting should look like shown below.
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/1efe0f50-93e3-4902-9af6-8a614374a7ff/Untitled.png)
    

### Screenshot Showing Connectivity Restored

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/dbbb3c8d-ed4b-48a8-a60e-f46535f4e3ed/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/cbe69941-8337-427c-8610-3da01a118fd1/1914c628-f33c-4ed7-9071-d7b9ca439a09/Untitled.png)

### Trying Another Website

- Repeat the steps to block and unblock a different website (e.g., `www.example.com`) to verify the firewall rules are effective.

### Conclusion

Testing firewall rules is essential for ensuring that security policies are properly enforced and network traffic is appropriately managed. By blocking and unblocking specific IP addresses, you can verify that your firewall is effectively controlling access as intended. These practices help maintain a secure network environment by ensuring that only authorized traffic is allowed and potential threats are effectively blocked.
