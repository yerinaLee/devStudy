```
[happytuk@ht-webapi06 fluentd]$ **echo happytuk5377! | sudo -S service fluentd stop**  
**[sudo] password for happytuk: fluentd stop**  

[happytuk@ht-webapi06 fluentd]$ ll  
total 8352536  
-rw-r--r--. 1 root root 8552920521 Apr 25 09:19 fluentd.log  

[happytuk@ht-webapi06 fluentd]$ **sudo rm -rf fluentd.log**  

[happytuk@ht-webapi06 fluentd]$ **echo happytuk5377! | sudo -S service fluentd start**  

[happytuk@ht-webapi06 fluentd]$ **tail -f fluentd.log**  
2025-04-25 09:19:39 +0800 [info]: #0 following tail of /var/log/happycode/api-req/couponApi/checkCreatePromotionAndCouponFromGameItemInventoryJSON/2025-04-25.txt  
2025-04-25 09:19:39 +0800 [info]: #0 following tail of /var/log/happycode/api-req/couponApi/createCouponUseHistoryJSON/2025-04-25.txt  
2025-04-25 09:19:39 +0800 [info]: #0 following tail of /var/log/happycode/api-req/couponApi/sendCouponItemJSON/2025-04-25.txt  
2025-04-25 09:19:39 +0800 [info]: #0 following tail of /var/log/happycode/api-req/couponApi/checkCouponJSON/2025-04-25.txt  
2025-04-25 09:19:39 +0800 [info]: #0 following tail of /var/log/happycode/api-req/couponApi/createPromotionAndCouponFromGameItemInventoryJSON/2025-04-25.txt  
2025-04-25 09:19:39 +0800 [info]: #0 following tail of /var/log/happycode/api-req/couponApi/deleteCouponUseHistoryJSON/2025-04-25.txt  
2025-04-25 09:19:39 +0800 [warn]: #0 /usr/local/tomcat7/logs/localhost_access_log.2025-04-25.txt already exists. use latest one: deleted #<struct Fluent::Plugin::TailInput::Entry path="/usr/local/tomcat7/logs/localhost_access_log.2025-04-25.txt", pos=168493109, ino=134759, seek=60>  
2025-04-25 09:19:39 +0800 [info]: #0 following tail of /usr/local/tomcat7/logs/localhost_access_log.2025-04-25.txt  
2025-04-25 09:19:39 +0800 [info]: #0 disable filter chain optimization because [Fluent::Plugin::RecordTransformerFilter] uses `#filter_stream` method.  
2025-04-25 09:19:39 +0800 [info]: #0 fluentd worker is now running worker=0
```