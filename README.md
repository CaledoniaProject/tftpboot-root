# tftpboot-root

支持 wakeonlan 远程激活

## TFTP 服务配置

Ubuntu 测试

```
cat > /etc/xinetd.d/tftp << EOF
service tftp
{
protocol        = udp
port            = 69
socket_type     = dgram
wait            = yes
user            = nobody
server          = /usr/sbin/in.tftpd
server_args     = /tmp/tftpboot
disable         = no
}
EOF

mkdir -p /tmp/tftpboot

apt-get install xinetd tftpd tftp -y
service xinetd restart
```

