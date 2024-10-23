### Steps to Resolve the DNS Issue

1. **Add A Record for www Subdomain**:
    
    - Log in to your domain registrar or DNS hosting provider's control panel.
    - Look for the DNS management section where you can manage your domain's records.
    - Add a new A record with the following details:
        - **Name**: `www` (or `www.bplandscapinginc.com`, depending on your DNS provider)
        - **Type**: A
        - **Value**: `52.201.237.113` (the public IP of your EC2 instance)

1. **Verify the DNS Changes**:
    
    - After adding the A record, it may take some time for DNS changes to propagate (usually a few minutes, but sometimes longer).
    - Once added, you can verify the new DNS record by running:
        
        `nslookup www.bplandscapinginc.com`
        
    - You should see the IP address `52.201.237.113` as the result.

1. **Retry Obtaining the SSL Certificate**:
    
    - After confirming that the DNS record for `www.bplandscapinginc.com` has been added and resolves correctly, run the Certbot command again:
        `sudo certbot --nginx -d bplandscapinginc.com -d www.bplandscapinginc.com`

### Summary

Adding the A record for the `www` subdomain should resolve the DNS problem you're encountering. Once that's done, you should be able to obtain your SSL certificate without any issues. If you run into further problems, feel free to ask!