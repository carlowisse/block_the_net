# Block The Net
> A collection of blocklists for ads, adult sites, trackers, social networks and telemetry endpoints.

## IP Tables
> I recommend adding the attached iptables to your device, this will speed up a lot of timeout issues commonly had with pihole.

```
sudo iptables -A INPUT -p tcp --dport 443 -j REJECT --reject-with tcp-reset
sudo iptables -A INPUT -p udp --dport 80 -j REJECT --reject-with icmp-port-unreachable
sudo iptables -A INPUT -p udp --dport 443 -j REJECT --reject-with icmp-port-unreachable

sudo ip6tables -A INPUT -p tcp --dport 443 -j REJECT --reject-with tcp-reset
sudo ip6tables -A INPUT -p udp --dport 80 -j REJECT --reject-with icmp6-port-unreachable
sudo ip6tables -A INPUT -p udp --dport 443 -j REJECT --reject-with icmp6-port-unreachable

sudo sh -c "iptables-save > /etc/iptables/rules.v4"
sudo sh -c "ip6tables-save > /etc/iptables/rules.v6"
```

## Install Additional Lists
```
sudo apt-get update

sudo apt install python3-pip

sudo pip3 install pihole5-list-tool --upgrade

sudo pihole5-list-tool
```