# frp
<h1>FRP (Fast Reverse Proxy)</h1>

✅ STEP–1: Update your system
sudo apt update && sudo apt upgrade -y

✅ STEP–2: Download FRP (latest version example: 0.56.0)

(You can check latest version on GitHub, but this works for most)

wget https://github.com/fatedier/frp/releases/download/v0.56.0/frp_0.56.0_linux_amd64.tar.gz

✅ STEP–3: Extract FRP
tar -xvf frp_0.56.0_linux_amd64.tar.gz


Go inside folder:

cd frp_0.56.0_linux_amd64

✅ STEP–4: Configure FRP Server (frps)

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

✅ STEP–5: Start FRP Server
./frps -c frps.ini


FRP server is now running on your VPS.

✅ STEP–6: Configure FRP Client (frpc)

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

✅ STEP–7: Start FRP Client
./frpc -c frpc.ini


Your local service on 8080 is now publicly available at:

YOUR_SERVER_IP:6000
