---
layout:     post
title:      如何实现基于UDP的socket通信
subtitle:   用java基于UDP实现socket通信
date:       2020-03-25
author:     irving.gx
header-img: img/post-bg-coffee.jpeg
catalog: true
tags:
    - Java,UDP,socket
---


# 前言
Java如何基于UDP实现server和client之间的通信，有以下方法可以参考


#### 发送端

   > 发送方`MyClient.java`
   
   ```java
   public class MyClient implements Runnable {

    //本机的IP
    private static final String ServerIP = "192.168.124.12" ;
    private static final int ServerPort = 4568;

    @Override
    public void run() {
        try {
            Thread.sleep(500);
        } catch (InterruptedException e1) {
            e1.printStackTrace();
        }
        try {
            InetAddress serverAddr = InetAddress.getByName(ServerIP );
            DatagramSocket socket = new DatagramSocket();
            byte[] buf;
            buf = ( "abc").getBytes();
            DatagramPacket packet = new DatagramPacket(buf, buf.length,
                serverAddr, ServerPort);
            socket.send(packet);
        } catch (Exception e) {
        }
    }
  }
   ```
#### 接收端

   > 接收数据的`MyServer.java`
   
   ```java
   public class MyServer implements Runnable {

    private static final String ServerIP = "192.168.124.12" ;
    private static final int ServerPort = 4568;
    @Override
    public void run() {
        try {
            InetAddress serverAddr = InetAddress.getByName(ServerIP);
            DatagramSocket socket = new DatagramSocket(ServerPort,serverAddr);
            byte[] buf = new byte[25];
            DatagramPacket packet = new DatagramPacket(buf, buf.length);
            socket.receive(packet);
            System.out.println(new String(packet.getData()).trim());
        } catch (Exception e) {
        }
    }
    }
   ```
#### 测试

   > 测试`Solution.java`
   
   ```java
   public class Solution{
    
      public static void main(String[] args){
          new Thread(new MyServer()).start();
          try {
              Thread.sleep(500);
          } catch (InterruptedException e) {

          }
          new Thread( new MyClient()).start();
      }
    }
   ```
    
运行Solution就可以在控制台看到服务端接收到的数据了。
  - - -
  <p align="center">如果对你有帮助，请作者喝一杯牛奶吧</p>
     
 ![image](https://raw.githubusercontent.com/GuoXinsayhello/GuoXinsayhello.github.io/master/img/wepay.jpg)
 
 


 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
  



        
  
  
  


 
 





