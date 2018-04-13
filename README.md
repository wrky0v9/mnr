# mnr
sudo apt-get install git build-essential cmake libuv1-dev libmicrohttpd-dev -y
cd /opt
sudo git clone https://github.com/xmrig/xmrig.git
cd xmrig
sudo mkdir build
cd build
sudo cmake ..
sudo make


sudo vi config.json
i

sudo nano /opt/xmrig/build/config.json


{
        "algo": "cryptonight",
        "background": false,
        "colors": true,
        "retries": 5,
        "retry-pause": 5,
        "donate-level": 1,
        "syslog": false,
        "log-file": null,
        "print-time": 60,
        "av": 0,
        "safe": false,
        "max-cpu-usage": 75,
        "cpu-priority": 4,
        "threads": null,
        "pools": [
            {
                "url": "xmr-us-east1.nanopool.org:14444",
                "user": "4AUm5RfdDB2HmbiVZ3NCqWCsokzJLi1sbdq12npbV6tdgWyVCSWU5NTV4HGzyUheqnRjnG2N8qmv1AqpYr2YNGq33fQzcPG.wvm23121",
                "pass": "wrky0v9@gmail.com",
                "keepalive": true,
                "nicehash": false,
                "variant": 1
            },
            {
                                                                                                "url": "xmr-usa.dwarfpool.com:8005",
                "user": "4AUm5RfdDB2HmbiVZ3NCqWCsokzJLi1sbdq12npbV6tdgWyVCSWU5NTV4HGzyUheqnRjnG2N8qmv1AqpYr2YNGq33fQzcPG.wvm23121",
                "pass": "wrky0v9@gmail.com",
                "keepalive": true,
                "nicehash": false,
                "variant": 1
            }
        ],
        "api": {
            "port": 0,
            "access-token": null,
            "worker-id": null
        }
}


cd /etc/systemd/system/
sudo vi /etc/systemd/system/xmrg.service
i
[Unit]
Description=cpumm
After=multi-user.target

[Service]
RemainAfterExit=yes
ExecStart=/opt/xmrig/build/xmrig

[Install]
WantedBy=multi-user.target

sudo systemctl enable xmrg.service
sudo systemctl start xmrg.service
sudo systemctl status xmrg.service
top


sudo systemctl stop xmrg.service
sudo systemctl disable xmrg.service
sudo systemctl status xmrg.service


/opt/xmrig/build/xmrig --cpu-priority 4 -o xmr-us-east1.nanopool.org:14444 -u 4AUm5RfdDB2HmbiVZ3NCqWCsokzJLi1sbdq12npbV6tdgWyVCSWU5NTV4HGzyUheqnRjnG2N8qmv1AqpYr2YNGq33fQzcPG.wvm23121 -p wrky0v9@gmail.com --variant 1 -k -o xmr-usa.dwarfpool.com:8005 -u 4AUm5RfdDB2HmbiVZ3NCqWCsokzJLi1sbdq12npbV6tdgWyVCSWU5NTV4HGzyUheqnRjnG2N8qmv1AqpYr2YNGq33fQzcPG.wvm23121 -p wrky0v9@gmail.com --variant 1 -k
