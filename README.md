# MunxEmail  
简介  
这是PHPMailer 6.0.6版本  
源码地址https://github.com/PHPMailer/PHPMailer.git  
#功能  
集成SMTP支持 - 无需本地邮件服务器即可发送  
发送包含多个To，CC，BCC和Reply-to地址的电子邮件  
添加附件，包括内联  
支持UTF-8内容和8bit，base64，二进制和引用可打印的编码  
通过SSL和SMTP + STARTTLS传输使用LOGIN，PLAIN，CRAM-MD5和XOAUTH2机制进行SMTP身份验证  
兼容PHP 5.5及更高版本  
自动验证电子邮件地址  
#使用方法  
composer require munx-email/munx-email dev-master   


class Mail{  
    public function sendMail($param, $code) {  
        // 实例化PHPMailer核心类  
        $mail = new PHPMailer();  
        // 是否启用smtp的debug进行调试 开发环境建议开启 生产环境注释掉即可 默认关闭debug调试模式    
        $mail->SMTPDebug = 1;    
        // 使用smtp鉴权方式发送邮件  
        $mail->isSMTP();  
        // smtp需要鉴权 这个必须是true  
        $mail->SMTPAuth = true;  
        // 链接qq域名邮箱的服务器地址  
        $mail->Host = 'smtp.qq.com';  
        // 设置使用ssl加密方式登录鉴权  
        $mail->SMTPSecure = 'ssl';  
        // 设置ssl连接smtp服务器的远程服务器端口号  
        $mail->Port = 465;  
        // 设置发送的邮件的编码  
        $mail->CharSet = 'UTF-8';  
        // 设置发件人昵称 显示在收件人邮件的发件人邮箱地址前的发件人姓名  
        $mail->FromName = '发件人姓名';  
        // smtp登录的账号 QQ邮箱即可  
        $mail->Username = '317083xxx@qq.com';  
        // smtp登录的密码 使用生成的授权码  
        $mail->Password = '需要去qq邮箱去开启smtp服务生成授权码';  
        // 设置发件人邮箱地址 同登录账号  
        $mail->From = '317083802@qq.com';  
        // 邮件正文是否为html编码 注意此处是一个方法  
        $mail->isHTML(true);  
        // 设置收件人邮箱地址  
        // $mail->addAddress('收件人的邮箱');  
        // 添加多个收件人 则多次调用方法即可  
        $mail->addAddress(收件人的邮箱);  
        // 添加该邮件的主题  
        $mail->Subject = '发送邮箱标题';  
        // 添加邮件正文  
        $mail->Body = '内容内容';  
        // 为该邮件添加附件  
        //$mail->addAttachment('./example.pdf');  
        // 发送邮件 返回状态 1为success  
        $res = $mail->send();  
        return $res;  
    }  

