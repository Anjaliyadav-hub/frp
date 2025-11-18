# frp
<h1>FRP (Fast Reverse Proxy)</h1>

✅ <h3>STEP–1: Update your system</h3>
sudo apt update && sudo apt upgrade -y
---

✅<h3> STEP–2: Download FRP (latest version example: 0.56.0)</h3>

(You can check latest version on GitHub, but this works for most)

wget https://github.com/fatedier/frp/releases/download/v0.56.0/frp_0.56.0_linux_amd64.tar.gz
---

✅ <h3>STEP–3: Extract FRP</h3>
tar -xvf frp_0.56.0_linux_amd64.tar.gz


Go inside folder:

cd frp_0.56.0_linux_amd64
---

✅ <h3>STEP–4: Configure FRP Server (frps)</h3>

Open frps.ini file:

nano frps.ini


Paste this:

[common]
bind_port = 7000
dashboard_port = 7500
dashboard_user = admin
dashboard_pwd = admin


Save & exit:
CTRL + O → ENTER → CTRL + X
---

✅<h3> STEP–5: Start FRP Server</h3>
./frps -c frps.ini


FRP server is now running on your VPS.
---

✅<h3> STEP–6: Configure FRP Client (frpc)</h3>

On your local system, create frpc.ini:

nano frpc.ini


Paste this:

[common]
server_addr = YOUR_SERVER_IP
server_port = 7000

[web]
type = tcp
local_port = 8080
remote_port = 6000


Save file.
---

✅ <h3>STEP–7: Start FRP Client</h3>
./frpc -c frpc.ini


Your local service on 8080 is now publicly available at:

YOUR_SERVER_IP:6000
![image alt](https://raw.githubusercontent.com/NishantDas0079/FRP-Cloud-Computing-/675c0c8e7dac65f035ef5c9386c5e5f6bd6623a8/IMG-20251109-WA0068.jpg)

----



