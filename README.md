### NTP Service Manual Installation

#### Compatible

- **Linux operation system** , CentOS 6-7, , Ubuntu18.04 , Debain10
- **Control panel**: No control panel , Direct admin  
If you are using a cPanel/WHM is not required install ntp service

#### Installation guide NTP Service 

  ##### Install for CentOS 6
```bash
yum install -y ntp
chkconfig ntpd on
cp /etc/ntp.conf /etc/ntp.conf.original
/etc/init.d/ntpd start
ntpstat
ntpq -p
```

  ##### Install for CentOS 7
  ```bash
yum install -y ntp
service ntpd enable
cp /etc/ntp.conf /etc/ntp.conf.original
systemctl start ntpd.service
ntpstat
ntpq -p
  ``` 

  ##### Install for  Ubuntu , Debain10
  ```bash
yum install -y ntp
service ntpd enable
mv /etc/ntp.conf /etc/ntp.conf.original
systemctl enable ntp
systemctl restart ntp
ntpstat
ntpq -p
  ```

###### Can used pool ntp server in thailand , edit in file ntp.conf inline 21-23

```bash
server time1.nimt.or.th iburst
server time2.nimt.or.th iburst
server time3.nimt.or.th iburst
```

###### Example Output ~ ntpq -p
```bash
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+110.78.24.101   .GPS.            1 u   15  256  377    1.731    0.030   0.028
+110.78.24.102   .IRIG.           1 u   26  256  377    1.882   -0.029   0.037
*110.78.24.103   .IRIG.           1 u  170  256  377    1.809    0.061   0.028
```
