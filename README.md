# tcpTOOL

import socket 
 import sys 
  
 print("İnstagram @ghost0x02 ") 
  
  
  
 def scanHost(ip, startPort, endPort): 
     print('Ana bilgisayarda TCP bağlantı noktası taraması başlatılıyor' % ip) 
     # TCP BAĞLANTI 
     tcp_scan(ip, startPort, endPort) 
     print('[+] %s ana bilgisayarında TCP taraması tamamlandı' % ip) 
  
 def scanRange(network, startPort, endPort): 
     print('[*] %s.0 ağında TCP bağlantı noktası taraması başlatılıyor' % network) 
     for host in range(1, 255): 
         ip = network + '.' + str(host) 
         tcp_scan(ip, startPort, endPort) 
  
     print('[+] %s.0 ağındaki TCP taraması tamamlandı' % network) 
  
  
 def tcp_scan(ip, startPort, endPort): 
     for port in range(startPort, endPort + 1): 
         try: 
             tcp = socket.socket(socket.AF_INET, socket.SOCK_STREAM) 
             if not tcp.connect_ex((ip, port)): 
                 print('[+] %s:%d/TCP Açık' % (ip, port)) 
                 tcp.close() 
         except Exception: 
             pass 
  
  
 def main(): 
     socket.setdefaulttimeout(0.01) 
     network = input("ip adresi: ") 
     startPort = int(input("bağlantı noktasını başlat: ")) 
     endPort = int(input("uç bağlantı noktası: ")) 
     scanHost(network, startPort, endPort) 
  
 main() 
 end = input("Kapatmak için herhangi bir tuşa basın.")
