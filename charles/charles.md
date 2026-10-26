# 1.Charles的功能简介
    Charles 是在 PC 端常用的网络封包截取工具，在做移动开发时，我们为了调试与服务器端的网络通讯协议，常常需要截取网络封包来分析。
    除了在做移动开发中调试端口外，Charles 也可以用于分析第三方应用的通讯协议。配合 Charles 的 SSL 功能，Charles 还可以分析 Https 协议。
    Charles 通过将自己设置成系统的网络访问代理服务器，使得所有的网络访问请求都通过它来完成，从而实现了网络封包的截取和分析。 

# 2.Charles下载地址
   (1)https://www.charlesproxy.com/download/
## 3.charles连接手机
  ### 3.1 charles上的配置
     （1）在 Charles 的菜单栏上选择 “Proxy”->”Proxy Settings”，填入代理端口 8888（或者自定义，前提是不能和系统已占用端口冲突），并且勾上 “Enable transparent HTTP proxying”
 <img width="1818" height="1334" alt="image" src="https://github.com/user-attachments/assets/4d95302e-bd89-4579-a93c-926940448362" />
     （2）在Mac上配置Charles证书，Charles菜单栏中的Help——SSL Proxying——Install Charles Root Certificate ，如果证书不受信任，请更改为完全信任
 <img width="1940" height="680" alt="image" src="https://github.com/user-attachments/assets/7960bbdd-2299-4670-9579-a58d7e43b0a2" />
 <img width="1702" height="584" alt="image" src="https://github.com/user-attachments/assets/5414cff0-d69c-4c94-a2f9-27acd052e628" />
      
 ### 3.2 手机上的配置
      （1）把charles的根证书下载到电脑上，通过其他软件 比如飞书或者wechat传给手机app，在手机上把根证书安装好，并在手机系统的设置里同意这个根证书，高版本ios：设置-通用-关于本机-滑倒最下面-证书信任设置-打开 Charles 开关
      （2）需要在charles上把手机的ip加入到可以同意抓包的ip里点击proxy-->Access Control Settings...
 <img width="1432" height="1360" alt="image" src="https://github.com/user-attachments/assets/8d7b0e32-d15a-4cd6-95b8-8c8dd46f1ede" />
      （3）如果charles弹出是都要同意手机ip的抓包的弹窗，点击同意
   <img width="1722" height="384" alt="image" src="https://github.com/user-attachments/assets/78cdc0c3-7263-4bdf-94bf-bdf16f9bb323" />
      （4）在手机系统的设置里，进行配置代理的设置，设置端口和电脑的服务器（端口就是刚才设置的8888，要和charles设置的端口对的上）
      <img width="1888" height="810" alt="image" src="https://github.com/user-attachments/assets/f9aa1b83-8513-465e-a28a-d675b2b44c29" />
        
# 4.charles的使用
   ## 4.1Map Remote
    远程映射，即：将「符合匹配规则」的请求映射向「一个远程地址」，可修改请求的寻址（url或ip+port）和路径（path），不可更改请求体内容
    开启前：通过Charles后，仍然请求向原定地址
    开启后：通过Charles后，向新远程地址请求
    
    选中Enable Map Remote→选中需要用到的map remote/点击add创建新的map remote→填写好要map remote的接口、通信协议、开发机的ip和端口号→点击ok
  <img width="1174" height="1080" alt="image" src="https://github.com/user-attachments/assets/df9867b5-2334-44d9-b20d-b721873dae94" />

   ## 4.2Map Local
    将接口的请求重定向到本地文件，此类操作可称为“Mock接口”
    本地映射，即：将「符合匹配规则」的请求映射向「一个本地文件」，请求完全在本机处理完成，不修改请求内容，响应为文件内容
    开启前：通过Charles后，仍然请求向原定地址                   
    开启后：通过Charles后，由Charles直接返回文件中的接口响应，不再与服务器通信
    
    选中Enable Map Local→选中需要用到的map local/点击add创建新的map local→填写好要map local的接口、对应的本地文件→点击ok
 <img width="1060" height="1088" alt="image" src="https://github.com/user-attachments/assets/8ed0fc78-2f05-4094-99b6-9e39d5d492d7" />

  ## 4.3Rewrite
    rewrite功能重写对应的内容，主要可以对某些匹配请求的header、host、url、path、query param、response status、body进行rewrite。
    改写，即：将「符合匹配规则」的请求，进行地址'、请求参数、请求Header、请求体、响应状态、响应体的增加、修改或删除操作

    选中Enable Rewrite→选中需要用到的rewrite/点击add创建新的rewrite→填写好要rewrite的地址接口、需要修改的值和修改后的值→点击ok
   <img width="626" height="522" alt="image" src="https://github.com/user-attachments/assets/169df105-bb3f-4129-b154-0a7940a25437" />
    <img width="2260" height="1038" alt="image" src="https://github.com/user-attachments/assets/ec3f31d9-da64-4b5b-a859-ee91e38bd681" />
    <img width="1793" height="980" alt="image" src="https://github.com/user-attachments/assets/ad5be957-3d7c-432e-9334-164e8b2edfb9" />

  ## 4.4Repeat
    重复发送请求
    是一手动操作，没有匹配规则的限制，可以自定义重复发送请求的并发、间隔等，但不能修改请求内容，即是“原样重发”。不需要客户端即可发送请求

   设置好后，Charles会重复发送指定次数的同一请求到服务器
   <img width="334" height="185" alt="image" src="https://github.com/user-attachments/assets/88557089-a2d8-4453-abc8-05cdbdcd86d1" />
   <img width="939" height="678" alt="image" src="https://github.com/user-attachments/assets/e3297058-5b90-483c-b8f0-ad8d146ba107" />

  ## 4.5Compose
   Compose功能是在原有的请求基础上进行修改。在进行接口测试时，临时需要修改请求参数、参数值或者Header等等就可以用到Compose功能。
   是一手动操作，没有匹配规则的限制，可以自定义编辑请求的地址，路径，参数，内容，header等，可手动点“Excute”按钮执行。
   和Repeat的功能、场景类似，区别在于，Compose可以编辑请求的内容，Repeat不可以
   不需要客户端即可发送请求

  选中想要临时修改参数的请求右键Compose→修改参数→Execute发送请求→收到响应
   <img width="1090" height="708" alt="image" src="https://github.com/user-attachments/assets/4b384f32-63fd-4570-9798-c0f16b0ca511" />

  ## 4.6Throttle Setting
   通过throttle setting可以模拟不同的网络环境
   <img width="716" height="666" alt="image" src="https://github.com/user-attachments/assets/5a4b0913-2b5b-4b1e-8e72-ce05118bdd23" />
   <img width="194" height="262" alt="image" src="https://github.com/user-attachments/assets/24fbea6b-6e77-4eec-aa6b-ebb872508e22" />
   <img width="430" height="482" alt="image" src="https://github.com/user-attachments/assets/5a4f922d-4a6d-43a6-b863-af888d9ebe11" />
   选中Enable Throttling→选择要模拟的网络环境→ok，设置好后就可以为连接代理的测试机模拟不同的网络

   
  ## 4.7Breakpoint
   断点，即：将「符合匹配规则」的请求中断，可选择在“请求”阶段或“响应”阶段中断，中断后，请求被暂时拦截到Charles，并展示请求详细界面供编辑、执行或丢弃
   breakpoint功能可以截取发送给服务器的请求以及服务器发送回的响应数据，截取成功后可以修改后继续发送。
   <img width="482" height="293" alt="image" src="https://github.com/user-attachments/assets/0d262ccf-68b9-4a48-ab2b-8327ef47f36d" />
   <img width="482" height="166" alt="image" src="https://github.com/user-attachments/assets/6fffdfea-cc7f-4a80-9a6e-357c9c9ad39c" />

   选中Enable Breakpoints→选中想要断点的请求、响应/点击add新建新的断点→OK。设置好后发往设置网址的请求或发回的响应就会被Charles截获，可以进行修改后继续发送。
   <img width="1200" height="839" alt="image" src="https://github.com/user-attachments/assets/62658207-dc13-4e5a-a96d-b46eb7f25bcb" />
   <img width="1200" height="835" alt="image" src="https://github.com/user-attachments/assets/457ddb18-20be-4e83-8fb3-928fb851f916" />



   

  
