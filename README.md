# fc00.org

Source code for http://www.fc00.org (http://h.fc00.org on Hyperboria).

## Sending your view of the network

In order to display accurate map of Hyperboria fc00 need your help. If you run CJDNS node, please send your network view using sendGraph.py script.

```bash
# Install requests and cjdns for Python 3
pip3 install cjdns requests
# Get the script
wget https://raw.githubusercontent.com/zielmicha/fc00.org/master/scripts/sendGraph.py
# Edit configuration
nano sendGraph.py
chmod +x sendGraph.py

# Run this every 20-100 minutes
./sendGraph.py
# For example, add it to crontab on Linux
(crontab -l; echo "@hourly /root/sendGraph.py") | crontab -
# or on FreeBSD
(crontab -l; echo "@hourly /usr/local/bin/python2 /root/sendGraph.py > /dev/null 2>&1") | crontab -
```

## Web server
```bash
git clone git@github.com:zielmicha/fc00.org.git
git clone git@github.com:zielmicha/nodedb.git web/nodedb
sudo apt-get install python-flask python-flup python-mysqldb python-pygraphviz

cd fc00.org/web
python web.py
```

Run `web/updateGraph.py` periodically to rerender nodes graph. You may want to customize reverse-proxy IP retrieval logic in web.py.
