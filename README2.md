# Born2Broot
This project has been created as part of the 42 curriculum by tphuwian.


# Password
Host = tphuwian42
Password(host) = Born2Broot42

Pharaphase = Born2Broot42

Sub user = tphuwian
Password(Sub user) = Born2Broot42

connect ssh with vm = ssh tphuwian@127.0.0.1 -p 4241
exit = exit

# Command

# theory
- What's debian vs rocky
Debian is an independent, stable distribution known as the "ancestor" of many others like Ubuntu. Its most recognizable feature is the use of the apt package manager and .deb files. For security, Debian implements AppArmor to manage program permissions, which is generally more straightforward to configure for new users.

On the other hand, Rocky Linux is designed for enterprise environments, serving as a 100% compatible successor to CentOS within the Red Hat (RHEL) family. It distinguishes itself by using the dnf package manager and .rpm files. For security, it employs SELinux, a powerful but highly complex system that is much more rigid compared to Debian's AppArmor.

Debian เปรียบเสมือนต้นตระกูลอิสระ (Independent) ที่เน้นความเรียบง่ายและเสถียรภาพสูงมาก จุดเด่นที่จำง่ายที่สุดคือการใช้ระบบจัดการซอฟต์แวร์ที่เรียกว่า apt ร่วมกับไฟล์ติดตั้งนามสกุล .deb ในด้านความปลอดภัย Debian จะใช้ระบบ AppArmor เป็นมาตรฐานเพื่อควบคุมสิทธิ์ของโปรแกรมต่าง ๆ ซึ่งเป็นมิตรกับผู้เริ่มต้นมากกว่า และมีชุมชนผู้ใช้งานขนาดใหญ่ที่คอยช่วยเหลือครับ

ในขณะที่ Rocky Linux ถูกสร้างขึ้นมาเพื่อเน้นการใช้งานในระดับองค์กร (Enterprise) โดยเฉพาะ โดยสืบทอดมาตรฐานมาจากตระกูล Red Hat (RHEL) เพื่อมาแทนที่ CentOS ที่เลิกพัฒนาไป ความแตกต่างที่ชัดเจนคือ Rocky จะใช้ระบบจัดการที่ชื่อว่า dnf (หรือ yum) และใช้ไฟล์ติดตั้งนามสกุล .rpm นอกจากนี้ในด้านความปลอดภัย Rocky จะเลือกใช้ SELinux ซึ่งมีความซับซ้อนและเข้มงวดในการตั้งค่ามากกว่า AppArmor ของ Debian อย่างมากครับ

- AppArmor vs SELinux

AppArmor (Application Armor) คือระบบความปลอดภัยที่เน้น "ความง่ายและความสะดวก" ในการใช้งาน โดยทำงานผ่านการระบุ Path (ที่อยู่ไฟล์) เป็นหลัก เช่น หากเราต้องการจำกัดสิทธิ์โปรแกรมใด เราก็เขียนกฎระบุไปเลยว่าห้ามเข้าถึงโฟลเดอร์ไหนบ้าง จุดเด่นคืออ่านเข้าใจง่าย (Human-readable) และเป็นระบบมาตรฐานที่ติดมากับ Debian ที่คุณกำลังใช้งานอยู่ครับ

ในทางกลับกัน SELinux (Security-Enhanced Linux) จะเน้นไปที่ "ความละเอียดและความเข้มงวด" ขั้นสูงสุด โดยไม่ได้มองที่ที่อยู่ไฟล์ แต่มองที่ Label (ป้ายกำกับ) ที่ติดไว้กับทุก Object ในระบบ (ไฟล์, พอร์ต, โปรเซส) หากป้ายกำกับไม่ตรงกัน ระบบจะไม่อนุญาตให้ทำงานเด็ดขาด SELinux จึงมีความซับซ้อนในการตั้งค่าสูงกว่ามาก แต่มันก็ให้ความปลอดภัยที่รัดกุมกว่า และเป็นมาตรฐานหลักของตระกูล Rocky Linux หรือ Red Hat ครับ

AppArmor focuses on simplicity and path-based security. It defines permissions based on the file paths that a program can access. Because the profiles are written in plain text and are relatively easy to understand, it is the preferred security module for Debian. It is "permissive" by default until a profile is explicitly created to restrict an application.
+1

SELinux, however, is a label-based Mandatory Access Control (MAC) system. Instead of file paths, it uses security labels (Contexts) assigned to every process and object. For an action to occur, the labels must match perfectly based on defined policies. While it offers more granular control and higher security, it is much more difficult to manage and is the standard for the Rocky Linux/RHEL family.

- UFW vs firewalld

UFW (Uncomplicated Firewall) ถูกออกแบบมาให้ "เรียบง่ายและตรงไปตรงมา" ตามชื่อเลยครับ จุดเด่นคือการสั่งงานที่เข้าใจง่าย เช่น หากต้องการเปิดพอร์ต 4242 คุณแค่พิมพ์ ufw allow 4242 UFW จะมองการตั้งค่าเป็นแบบ "รายการคำสั่ง" (Command-based) และเป็นเครื่องมือมาตรฐานที่ใช้ใน Debian

firewalld จะมีความ "ยืดหยุ่นและซับซ้อน" กว่ามาก โดยใช้แนวคิดที่เรียกว่า Zones (โซน) ในการจัดการ แทนที่จะสั่งเปิดพอร์ตเฉยๆ คุณต้องเลือกว่าจะให้ Interface ไหนอยู่ในโซนอะไร (เช่น Public, Home, หรือ Work) ซึ่งแต่ละโซนจะมีกฎต่างกัน firewalld สามารถเปลี่ยนการตั้งค่าได้แบบ Real-time โดยไม่ต้องรีสตาร์ทเซอร์วิส และเป็นเครื่องมือมาตรฐานของตระกูล Rocky Linux ครับ

UFW (Uncomplicated Firewall) is built for simplicity and ease of use. It provides a CLI that is very easy to remember, such as ufw allow 4242 to open your required port. It acts as a wrapper for iptables and is the default firewall management tool for Debian.

firewalld, on the other hand, is a dynamic firewall manager that uses the concept of Zones to define the trust level of network connections. It allows for more complex configurations where different network interfaces can have different security rules simultaneously. Unlike UFW, firewalld supports runtime configuration changes without dropping existing connections and is the standard for Rocky Linux/RHEL.

- VirtualBox vs UTM

VirtualBox เป็นโปรแกรมประเภท Virtualization แบบดั้งเดิมที่เน้นความเข้ากันได้สูง หากคุณใช้เครื่อง Mac ที่เป็นชิป Intel การใช้ VirtualBox จะทำได้ลื่นไหลมากเพราะจำลองสถาปัตยกรรมเดียวกัน (x86) จุดเด่นคือมีฟีเจอร์ที่ครบถ้วนสำหรับการเรียนรู้เรื่อง Network และการจัดการ Snapshot ที่ละเอียด ซึ่งเป็นเหตุผลที่นักเรียนส่วนใหญ่เลือกใช้ในโปรเจกต์นี้ครับ

UTM ถูกออกแบบมาเพื่อเครื่อง Mac ยุคใหม่ (ชิป Apple Silicon/M1/M2/M3) โดยเฉพาะ UTM มีจุดเด่นคือสามารถทำได้ทั้ง Virtualization (รันเร็วมากถ้าเป็นระบบ ARM เหมือนกัน) และ Emulation (จำลองสถาปัตยกรรมอื่น เช่น รัน Debian x86 บนเครื่อง M1) UTM ใช้เทคโนโลยี Apple Hypervisor Framework ทำให้ประหยัดพลังงานและทำงานร่วมกับระบบปฏิบัติการ macOS ได้อย่างแนบเนียนกว่าครับ

VirtualBox is a robust Virtualization tool that has been the industry standard for a long time. It excels on Intel-based Macs by allowing the Guest OS to run directly on the host's hardware with high efficiency. For the Born2beRoot project, it offers advanced networking features and snapshot management that are very helpful for testing and defense.

UTM is specifically optimized for Apple Silicon (M-series) Macs. It utilizes Apple's Hypervisor framework to deliver high performance when virtualizing ARM-based operating systems. A key feature of UTM is its ability to perform Emulation, allowing you to run x86 operating systems on an ARM Mac, though this process is much slower than direct virtualization.
--------------------------------------------------------

# Project overview

1. ภาคทฤษฎี: ความเข้าใจพื้นฐาน (Project Overview)
หัวข้อนี้ผู้ตรวจจะให้คุณอธิบายหลักการทำงานเบื้องต้น หากตอบไม่ชัดเจน การตรวจจะหยุดลงทันที (Evaluation stops here) ครับ

ภาษาไทย:

Virtual Machine (VM) คืออะไร: คือการจำลองคอมพิวเตอร์อีกเครื่องหนึ่งขึ้นมาซ้อนบนเครื่องจริง (Physical Machine) โดยใช้ทรัพยากร (CPU, RAM, Disk) ร่วมกัน

ทำไมต้องใช้ VM: เพื่อความปลอดภัย (Isolate environment), การทดสอบระบบปฏิบัติการที่ต่างกันโดยไม่ต้องลงเครื่องใหม่ และประหยัดทรัพยากรฮาร์ดแวร์

Rocky vs Debian:

Debian: เน้นความเสถียร (Stable) และความง่ายในการจัดการแพ็กเกจ

Rocky: เป็นตระกูล RHEL (Red Hat) เน้นใช้งานในระดับองค์กร (Enterprise)

Apt vs Aptitude (สำหรับ Debian): apt เป็นเครื่องมือพื้นฐานที่ใช้งานง่าย ส่วน aptitude เป็นเวอร์ชันที่ฉลาดกว่าในการจัดการความขัดแย้งของไฟล์ (Dependencies)

AppArmor คืออะไร: เป็นระบบความปลอดภัยของ Linux ที่ช่วยจำกัดสิทธิ์ของโปรแกรมไม่ให้ทำอะไรเกินขอบเขตที่กำหนด
- #####
เช็ค Hostname: ใช้คำสั่ง hostnamectl เพื่อยืนยันว่าชื่อเครื่องคือ tphuwian42

เช็คการเชื่อมต่อ SSH: แสดงให้เห็นว่าเข้าผ่านพอร์ต 4242 ได้จริง

เช็คสิทธิ์ User: ใช้คำสั่ง groups tphuwian เพื่อดูว่าอยู่ใน group user42 หรือยัง
#####
# Cron (time fileds)
  ┌───────────── นาที (0 - 59)
  │ ┌─────────── ชั่วโมง (0 - 23)
  │ │ ┌───────── วันที่ (1 - 31)
  │ │ │ ┌─────── เดือน (1 - 12)
  │ │ │ │ ┌───── วันในสัปดาห์ (0 - 6) (0 คือวันอาทิตย์)
  │ │ │ │ │
  * * * * * /path/to/command

###
คำสั่งตรวจสอบ Cron: sudo crontab -u root -l (เพื่อแสดงเวลา */10 * * * *)

การอธิบายสคริปต์: คุณต้องอธิบายได้ว่าสคริปต์ดึงค่า RAM, Disk และ CPU มาแสดงผลอย่างไรบนหน้าจอทุก Terminal

1. What is a Virtual Machine: A simulation of a computer system that runs as a guest on top of a physical host machine, sharing its resources.

Purpose of VM: For security isolation, testing different operating systems without hardware changes, and resource efficiency.

Rocky vs Debian: Debian focuses on stability and package management ease, while Rocky is an enterprise-grade OS based on RHEL.

Apt vs Aptitude: apt is the standard package manager, whereas aptitude is more advanced at handling complex dependencies.

What is AppArmor: A Linux kernel security module that restricts programs' capabilities to enhance system security.
###
Check Hostname: Use hostnamectl to verify the system name is tphuwian42.

Verify SSH Connection: Demonstrate successful login via port 4242.

Check User Groups: Run groups tphuwian to confirm membership in the user42 group.
###
# Cron (time fileds)
  ┌───────────── นาที (0 - 59)
  │ ┌─────────── ชั่วโมง (0 - 23)
  │ │ ┌───────── วันที่ (1 - 31)
  │ │ │ ┌─────── เดือน (1 - 12)
  │ │ │ │ ┌───── วันในสัปดาห์ (0 - 6) (0 คือวันอาทิตย์)
  │ │ │ │ │
  * * * * * /path/to/command
###
Checking and Explaining
Command to check Cron: # sudo crontab -u root -l (to display the */10 * * * * schedule).

Script Explanation: You must be able to explain how the script retrieves RAM, Disk, and CPU values to display them across all terminals.
# Simple setup

- Theory 
GUI Check: เครื่องต้องไม่มีสภาพแวดล้อมแบบกราฟิก (No Graphical Environment) ตอนเริ่มทำงาน เพื่อให้เป็นเซิร์ฟเวอร์ที่แท้จริง

User Check: ห้ามล็อกอินหรือเชื่อมต่อด้วย root โดยตรง ต้องใช้ User ปกติเท่านั้น

Password Rules: รหัสผ่านที่เลือกต้องทำตามกฎความปลอดภัยที่โจทย์กำหนด (เช่น มีความยาว มีตัวใหญ่ ตัวเล็ก และตัวเลข)

OS Choice: ต้องอธิบายได้ว่าทำไมถึงเลือก Debian (เช่น เน้นความเสถียร) หรือ Rocky (เน้นใช้งานระดับองค์กร)

1. ตรวจสอบการล็อกอินและสถานะเครื่อง

ตรวจสอบ User ที่กำลังใช้งาน = whoami
ตรวจสอบว่าระบบรันอยู่ในโหมด Text (Multi-user) ไม่ใช่ GUI = systemctl get-default

2. ตรวจสอบการทำงานของ Firewall (UFW)

ตรวจสอบสถานะการทำงานของ UFW = sudo ufw status

หรือเช็คสถานะผ่าน systemctl = sudo systemctl status ufw

3. ตรวจสอบการทำงานของ SSH

ตรวจสอบสถานะบริการ SSH = sudo service ssh status

หรือเช็คพอร์ตที่ SSH กำลังฟังอยู่ (ต้องเป็น 4242) = ss -tunlp | grep 4242

4. ตรวจสอบระบบปฏิบัติการ (Operating System)

ตรวจสอบรายละเอียด OS และเวอร์ชัน = hostnamectl

----------------------------------------------------
# user set up

How a VM works = การใช้ซอฟต์แวร์จำลองทรัพยากรฮาร์ดแวร์ (CPU, RAM) เพื่อรันระบบปฏิบัติการซ้อนบนเครื่องจริง

Using software to emulate hardware resources to run a guest OS on a physical host.

Purpose of VMs = เพื่อความปลอดภัย (Isolation), การทดสอบระบบในสภาพแวดล้อมที่ต่างกัน และประหยัดฮาร์ดแวร์	

For security isolation, testing in different environments, and optimizing hardware use.

Choice of OS = เลือก Debian เพราะมีความเสถียรสูง (Stable) และเป็นที่นิยมสำหรับระบบเซิร์ฟเวอร์	

Choosing Debian for its high stability and popularity in server environments.

Rocky vs Debian	Debian = เป็นต้นแบบของหลาย OS และจัดการง่าย ส่วน Rocky เน้นมาตรฐานองค์กร 
(Enterprise)	Debian is a community-driven stable base; Rocky is an enterprise-grade OS.

Aptitude vs Apt	aptitude  = ฉลาดกว่าในการแก้ปัญหาความขัดแย้งของไฟล์ (Dependencies) เมื่อเทียบกับ apt	
aptitude handles complex dependency conflicts better than the standard apt tool.

AppArmor = ระบบความปลอดภัยที่คุมสิทธิ์การเข้าถึงทรัพยากรของโปรแกรมเพื่อป้องกันการบุกรุก	
A security framework that restricts program access to enhance system protection.

1. ตรวจสอบการบูตและผู้ใช้งาน (Login & UI Check)
ตอนที่ใช้: เมื่อเริ่มเปิดเครื่องเพื่อโชว์ว่าไม่มีหน้าจอ GUI

# ยืนยันว่าระบบอยู่ในโหมดข้อความ (Text Mode)
systemctl get-default
# ผลลัพธ์ที่ถูกต้อง: multi-user.target

# เช็คว่าล็อกอินด้วย User ปกติ (ไม่ใช่ root)
whoami
# ผลลัพธ์: tphuwian

2. ตรวจสอบการทำงานของ Firewall (UFW)
ตอนที่ใช้: ยืนยันว่า Firewall เริ่มทำงานแล้วและป้องกันพอร์ตที่ไม่เกี่ยวข้อง

# ตรวจสอบสถานะการทำงานของ UFW
sudo ufw status
# ผลลัพธ์: Status: active

3. ตรวจสอบบริการ SSH (SSH Service)
ตอนที่ใช้: ยืนยันว่า SSH พร้อมให้เชื่อมต่อผ่านพอร์ต 4242

# ตรวจสอบว่าบริการ SSH รันอยู่จริง
sudo systemctl status ssh

# ตรวจสอบพอร์ตที่ SSH กำลังฟังอยู่
ss -tunlp | grep 4242

4. ตรวจสอบระบบปฏิบัติการ (OS Verification)
ตอนที่ใช้: ยืนยันเวอร์ชันของระบบปฏิบัติการ

# แสดงข้อมูล OS และรายละเอียดระบบ
hostnamectl

---------------------------------------------------

# User setup 2

1. การตรวจสอบ UI และ User
เป้าหมาย: ยืนยันว่าไม่มีหน้าต่างกราฟิก (GUI) และไม่ได้ใช้ root

# เช็คว่าล็อกอินด้วย User ปกติ (ไม่ใช่ root)
whoami

# ยืนยันว่าระบบรันอยู่ในโหมดข้อความ (Text Mode)
systemctl get-default
# ผลลัพธ์ที่ถูกต้อง: multi-user.target

2. การตรวจสอบ Service สำคัญ
เป้าหมาย: ยืนยันว่า UFW (Firewall) และ SSH ทำงานอยู่

# ตรวจสอบสถานะ Firewall (ต้องเป็น active)
sudo ufw status

# ตรวจสอบว่าบริการ SSH รันอยู่จริง
sudo systemctl status ssh

3. การตรวจสอบระบบปฏิบัติการ
# แสดงข้อมูล OS และรายละเอียดระบบ
hostnamectl

-----------------------------------------------

# Hostname and partitions

1. การตรวจสอบการบูตและผู้ใช้งาน (Boot & User Check)
ตอนที่ใช้: ยืนยันว่าไม่มีหน้าจอแบบกราฟิก (Graphical environment) และล็อกอินด้วย User ปกติที่ไม่ใช่ Root


# ตรวจสอบว่าระบบรันอยู่ในโหมดข้อความ (Text mode)
systemctl get-default 
# ผลลัพธ์ต้องเป็น: multi-user.target (ไม่ใช่ graphical.target)

# ตรวจสอบว่าไม่ได้ใช้ Root (Non-root user)
whoami 
# ผลลัพธ์ต้องเป็นชื่อ User ของคุณ (เช่น tphuwian)

2. การตรวจสอบไฟร์วอลล์ (UFW Service Check)
ตอนที่ใช้: ยืนยันว่าระบบป้องกันเริ่มทำงานแล้ว (Started)

# ตรวจสอบสถานะการทำงานของ UFW (Firewall status)
sudo ufw status 
# ผลลัพธ์ต้องขึ้น: Status: active

3. การตรวจสอบบริการเชื่อมต่อระยะไกล (SSH Service Check)
ตอนที่ใช้: ยืนยันว่าบริการ SSH พร้อมทำงานบนพอร์ตที่กำหนด

# ตรวจสอบว่าบริการ SSH รันอยู่จริง (Service status)
sudo systemctl status ssh 
# ผลลัพธ์ต้องขึ้น: active (running)

# ตรวจสอบพอร์ตที่กำลังใช้งาน (Listening port)
ss -tunlp | grep 4242 
# ต้องเห็นว่าพอร์ต 4242 ถูกใช้งานอยู่

4. การตรวจสอบระบบปฏิบัติการ (Operating System Check)
ตอนที่ใช้: ยืนยันเวอร์ชันของ OS ตามที่เลือกไว้ (Debian หรือ Rocky)

# แสดงข้อมูล OS และรายละเอียดระบบ (System info)
hostnamectl

---------------------------------------------------

# sudo

# Reccommend
1. User step 1 & 2: การจัดการผู้ใช้และนโยบายรหัสผ่าน
ผู้ตรวจจะให้คุณสร้างผู้ใช้ใหม่และตรวจสอบว่ามีการบังคับใช้กฎรหัสผ่านตามที่โจทย์สั่งหรือไม่

ทฤษฎี (Theory): ข้อดีของการมีนโยบายรหัสผ่าน (Password Policy) คือช่วยลดความเสี่ยงจากการถูกโจมตีแบบ Brute-force และการคาดเดารหัสผ่านได้ง่าย ข้อเสียคือผู้ใช้อาจลืมรหัสผ่านหรือจดบันทึกรหัสผ่านไว้ในที่ที่ไม่ปลอดภัยเนื่องจากความซับซ้อน

# การสร้างผู้ใช้ใหม่และกลุ่ม (User step 1 & 2)
sudo adduser <ชื่อผู้ใช้ใหม่>        # สร้าง user ใหม่ (ระบุ password ตามกฎ)

sudo groupadd evaluating           # สร้าง group ใหม่ชื่อ "evaluating"

sudo usermod -aG evaluating <ชื่อผู้ใช้ใหม่>  # เพิ่ม user เข้ากลุ่ม

# การตรวจสอบสิทธิ์และกลุ่ม (User step 1)
groups tphuwian                   # ต้องมีกลุ่ม 'sudo' และ 'user42'

2. Hostname and partitions: ชื่อเครื่องและการจัดสรรดิสก์
ส่วนนี้เน้นการแก้ไขชื่อเครื่องและการอธิบายหลักการทำงานของ LVM

ทฤษฎี (Theory): LVM (Logical Volume Management) คือการจัดการดิสก์ที่ยืดหยุ่นกว่าพาร์ทิชันปกติ ประกอบด้วย Physical Volume (PV), Volume Group (VG) และ Logical Volume (LV) ซึ่งช่วยให้เราสามารถขยายหรือลดขนาดพื้นที่ได้โดยไม่ต้องฟอร์แมตดิสก์ใหม่

# การตรวจสอบและแก้ไข Hostname
hostname                          # ตรวจสอบชื่อปัจจุบัน (ต้องเป็น tphuwian42)
sudo hostnamectl set-hostname <ชื่อใหม่>  # แก้ไขชื่อเครื่องตามที่ผู้ตรวจสั่ง

# การตรวจสอบพาร์ทิชัน
lsblk                             # แสดงโครงสร้างพาร์ทิชันและ LVM

# Realpart

3. SUDO: สิทธิ์การบริหารจัดการระบบ
ผู้ตรวจจะตรวจสอบว่าโปรแกรม sudo ถูกติดตั้งและตั้งค่ากฎความปลอดภัยพร้อมการเก็บ Log อย่างถูกต้อง

ทฤษฎี (Theory): sudo (superuser do) คือคำสั่งที่อนุญาตให้ผู้ใช้ทั่วไปรันโปรแกรมด้วยสิทธิ์ของ root ได้ตามกฎที่กำหนดไว้ในไฟล์ /etc/sudoers เพื่อความปลอดภัยในการบริหารจัดการระบบ

# ตรวจสอบการติดตั้งและการตั้งค่ากลุ่ม
dpkg -l | grep sudo               # เช็คว่ามีโปรแกรม sudo ติดตั้งอยู่

sudo usermod -aG sudo <ชื่อผู้ใช้ใหม่> # เพิ่ม user ใหม่เข้ากลุ่ม sudo

# การตรวจสอบ LOGS (ส่วนนี้สำคัญมาก)
ls /var/log/sudo/                 # ต้องมีโฟลเดอร์นี้และมีไฟล์ Log อย่างน้อยหนึ่งไฟล์

sudo cat /var/log/sudo/<ไฟล์ log>   # แสดงประวัติการใช้คำสั่ง sudo ที่ผ่านมา

------------------------------------------------------------

# UFW / Firewalld

1. การตรวจสอบการบูตและผู้ใช้งาน (Login & UI Check)
เมื่อไหร่ที่ใช้:เมื่อเริ่มเปิดเครื่องเพื่อโชว์ว่าไม่มีหน้าจอ GUI และไม่ได้ใช้ root

# ยืนยันว่าระบบอยู่ในโหมดข้อความ (Text Mode) ไม่ใช่หน้าต่างกราฟิก
systemctl get-default
# เช็คว่าล็อกอินด้วย User ปกติ (ไม่ใช่ root)
whoami

2. การตรวจสอบการทำงานของ Firewall (UFW)
เมื่อไหร่ที่ใช้: ยืนยันว่า Firewall เริ่มทำงานแล้ว (Started)

# ตรวจสอบสถานะการทำงานของ UFW (ต้องขึ้น Status: active)
sudo ufw status

3. การตรวจสอบบริการ SSH (SSH Service)
เมื่อไหร่ที่ใช้: ยืนยันว่าบริการ SSH พร้อมทำงานบนพอร์ตที่กำหนด

# ตรวจสอบว่าบริการ SSH รันอยู่จริง
sudo systemctl status ssh
# ตรวจสอบพอร์ตที่ SSH กำลังฟังอยู่ (ต้องเป็น 4242)
ss -tunlp | grep 4242

4. การตรวจสอบระบบปฏิบัติการ (OS Verification)
เมื่อไหร่ที่ใช้: ยืนยันเวอร์ชันและชื่อเครื่อง (Hostname)

# แสดงข้อมูล OS และรายละเอียดชื่อเครื่อง
hostnamectl

------------------------------------------------------------

# ssh

ภาคทฤษฎี (Theory)
SSH คืออะไร: คือโปรโตคอล (Protocol) สำหรับการเชื่อมต่อเพื่อควบคุมคอมพิวเตอร์ระยะไกลแบบเข้ารหัส เพื่อความปลอดภัยในการบริหารจัดการระบบ

ทำไมต้องเปลี่ยนพอร์ตเป็น 4242: เพื่อความปลอดภัย (Security through obscurity) เพราะพอร์ตมาตรฐาน 22 มักตกเป็นเป้าหมายของการโจมตี

ทำไมต้องห้าม root login: เพื่อป้องกันการสุ่มรหัสผ่าน (Brute-force) เข้าสู่บัญชีที่มีสิทธิ์สูงสุดของระบบโดยตรง

# ตรวจสอบการติดตั้งและสถานะ:
# เช็คว่าบริการ SSH ติดตั้งและรันอยู่ปกติหรือไม่
sudo service ssh status

# ตรวจสอบพอร์ตที่ใช้งาน (Port Verification):
# ยืนยันว่า SSH ใช้เฉพาะพอร์ต 4242 เท่านั้น
grep "Port" /etc/ssh/sshd_config
# หรือเช็คพอร์ตที่กำลัง Listening อยู่จริง
ss -tunlp | grep 4242

ทดลองเชื่อมต่อด้วย User ใหม่: ผู้ตรวจจะให้คุณลองใช้ User ที่สร้างขึ้นใหม่ (จากขั้นตอน User step 1) เชื่อมต่อผ่าน SSH จากเครื่อง Mac:
# พิมพ์คำสั่งนี้บน Terminal ของเครื่อง Mac
ssh <ชื่อuserใหม่>@127.0.0.1 -p 4241

ยืนยันการห้าม Root Login:
# แสดงไฟล์การตั้งค่าว่า PermitRootLogin ถูกตั้งเป็น no
grep "PermitRootLogin" /etc/ssh/sshd_config

-------------------------------------------------------

# Script mirroring 

How your script works (การทำงานของสคริปต์):

ภาษาไทย: อธิบายว่าสคริปต์ของคุณดึงค่าต่างๆ มาจากไหน (เช่น ใช้คำสั่ง free ดู RAM, df ดู Disk usage) และใช้คำสั่ง wall เพื่อประกาศข้อความออกไปทุก Terminal

English: Explain how your script retrieves system data (e.g., using free for RAM, df for Disk) and uses the wall command to broadcast information to all logged-in users.

What is "cron"? (Cron คืออะไร):

ภาษาไทย: คือซอฟต์แวร์อรรถประโยชน์ (Utility) ที่ใช้สำหรับตั้งเวลาการทำงานของคำสั่งหรือสคริปต์ให้รันโดยอัตโนมัติ ตามเวลาหรือรอบวันที่กำหนด

English: A time-based job scheduler in Unix-like operating systems that runs commands or scripts automatically at fixed times, dates, or intervals.

1. ตรวจสอบการตั้งเวลา (Verify 10-minute interval)
ตอนที่ใช้: แสดงให้เห็นว่าสคริปต์ถูกตั้งให้รันทุก 10 นาทีตั้งแต่เปิดเครื่อง
sudo crontab -u root -l (Output = */10 * * * *)

2. การเปลี่ยนความถี่ (Verify dynamic values)
ตอนที่ใช้: ผู้ตรวจจะให้คุณเปลี่ยนจากทุก 10 นาที เป็นทุกๆ 1 นาที เพื่อให้เห็นว่าค่าที่แสดงผล (Dynamic values) เปลี่ยนไปจริงๆ หรือไม่

sudo crontab -u root -e
 then change from */10 to * or */1

 3. การหยุดสคริปต์ (Stop without modifying the script)
ตอนที่ใช้: ผู้ตรวจจะให้คุณสั่งหยุดสคริปต์โดย "ห้ามเข้าไปแก้ไขไฟล์สคริปต์"

sudo service cron stop
# หรือ
sudo systemctl stop cron

4. ขั้นตอนสุดท้าย: การตรวจสอบความคงเดิม (Final Restart)
เป้าหมาย: Restart เครื่องหนึ่งครั้งเพื่อพิสูจน์ว่า:

1.สคริปต์ยังอยู่ที่เดิม (Same place)

2.สิทธิ์การเข้าถึงไฟล์ยังเหมือนเดิม (Rights unchanged)

3.ไฟล์ไม่ได้ถูกแอบแก้ไข (Not modified)

ls -l /path/to/your/monitoring.sh

--------------------------------------


# Port
check port which one is work = ss -tunlp | grep 4242
check file = grep "Port" /etc/ssh/sshd_config

# #Install_sudo
su
*ไว้สำหรับเปลี่ยนเป็น root*
apt install sudo
*ไว้สำหรับโหลด Package*
sudo reboot 
*ไว้สั่งให้เครื่อง Restart*
sudo -V
*เป็นการเช็กเวอร์ชันของ sudo ที่โหลดมาว่าเป็นเวอร์ชันไหน*
sudo shutdown now(อันนี้แถม)
*สั่งให้ปิดเครื่อง*

# #Create_a_user
sudo adduser [login]
*ไว้สร้าง User ใหม่ขึ้นมา*
sudo addgroup user42
*ไว้สร้างกลุ่มที่ชื่อว่าuser42*
![[Pasted image 20251224002556.png]]
(GID คือ Group ID)
getent group [groupname]
*ดูว่าเราได้ทำการสร้างกลุ่มนั้นมารึ้ยัง (getent เป็นการเช็ก)*

# #Adding_a_user_to_a_group
sudo adduser [username] (groupname)
*เอาuser ไปใส่ลงใน group นั้น*
sudo adduser tphuwian42 sudo
sudo adduser tphuwian42 user42
getent group sudo user42

# #Instal_ConfigSSH
sudo apt update
*สำหรับอัพเดตสิ่งที่เพิ่มเข้ามาใหม่ใน  sudo*

sudo apt install openssh-server
*ให้สามารถเชื่อมต่อกับคอมพิวเตอร์ได้ในระยะไกลเหมือน Remote*

sudo service ssh status
*ดูว่า ssh นั้นกำลังทำงานอยู่รึเปล่า*

su nano /etc/ssh/sshd_config
 *ไปเปิดเพื่อแก้ไขไฟล์ของ sshd
 /etc/ เป็นโฟลเดอร์ไว้เก็บ Config ของระบบ
 ssh/ โฟลเดอร์ของ ssh
 sshd_config เป็นไฟล์ที่เราจะเข้าไปแก้ไข*
 (ssh เป็นตัวที่ใช้ remote ส่วน sshd ก็คือ ssh daemon เป็นตัวเซิฟ)
sudo service ssh restart
*ไว้รีของ ssh*
sudo service ssh status
*ดูสถานะว่าเป็น 4242 ไหม*

# Intasll_Config_UFW
sudo apt install ufw
*โหลด ufw*
sudo ufw enable
*เปิดใช้งาน ufw*
sudo ufw allow 4242
*ไว้เปิิดพื่ออนุญาติให้ใช้ได้*
sudo ufw status
*ดูสถานะ*

# sudo_policies
touch /etc/sudoers.d/sudo_config

*touch ไว้สร้างไฟล์ใหม่
/etc มาจาก Etcetera เป็นเหมือนที่ไว้เก็บไฟล์สำคัญๆ

sudoers คือชื่อของระบบจัดการสิทธิ์
.d มาจาก Direcotry ที่บอกว่าจะเก็บค่าเพิ่มเติมนะ
sudo_config เป็นชื่อไฟล์ที่จะใส่
สรุปคือไว้สำหรับสร้างไฟล์เปล่าไว้ในโฟลเดอรื /etc/sudoers.d/
*
mkdir /var/log/sudo
*mkdir ไว้สร้างโฟลเดอร์
/var คือโฟลเดอร์ของ linux ที่มีขนาดยืดหดได้ตลอดเวลา เปลี่ยนแปลวข้างในได้(เป็นไฟล์ทีร่เปลี่ยนแปลงบ่อยครั้งระหว่างทำงาน เช่น บันทึกไฟล์ /var/log
/log/ มาจาก log files  ไว้เก็บพวกประวัติต่างๆ
sudo เป็นโฟลเดอร์ที่เลือกว่าจะเก็บ((เราสร้าง)
*
nano /etc/sudoers.d/sudo_config
*nano เป็นการแก้ไขไฟล์*

Defaults  passwd_tries=3
Defaults  badpass_message="Mensaje de error personalizado"(มาจากภาษาสเปนที่แปลว่า Custom error message)
Defaults  logfile="/var/log/sudo/sudo_config"
Defaults  log_input, log_output
Defaults  iolog_dir="/var/log/sudo"
Defaults  requiretty
Defaults  secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"
*passwd_tries=3 :ใส่รหัสได้ทั้งหมด3ครั้ง
badpass_message : เป็นการแจ้งเตือนเกี่ยวกับรหัส
logfile : บอกที่อยู่ของไฟล์
log_input/output : สั่งให้บันทึกทุกอย่างที่พิมพ์เข้าไป (Input) และ ที่อย่างที่แสดงผลออกมา (Output)
(อันนี้ละเอียดมากเพราะจะบันทึกคลิปวีดีโอจากหน้าจอ Terminal ว่าเราทำอะไรบ้าง)
iolog_dir : บอก folder
requiretty : บังคับให้รันผ่าน TTY (Terminalเท่านั้น) ไว้ป้องกันไม่ให้  Sript อัตรโนมัติหรือโปรแกรมส่วนหลังที่ใช้ sudo ไม่ให้เรารู้
secure_path : กำหนดเส้นทางที่ปลอดภัยสำหรับรันผ่าน sudo เช่น ถ้ามีคนแอบเอาไวรหัสชื่อ ls ไว้ ทีนี้พอพิมพ์ sudo ls ก็จะเป็นการรันไวรัสบน root

 สรุป : จำกัดกรอกรหัสผิดไม่เกิน 3 ครั้ง และมีข้อความแจ้งเตือน และมีการเก็บ Log ไว้เพื่อตรวจสอบย้อนหลังได้ละเอียด และบังคับให้รันผ่าน Terminalเท่านั้น(req) จำกัด path ในการใช้งาน*

 # Password_policy
nano /etc/login.defs
*เปิดเพื่อแก้ไขไฟล์
เปลี่ยน PASS_MAX_DAYS จาก 99999 เป็น30 เหมือนเป็นการบังคับให้เปลี่ยนรหัสทุกๆเดือนแทนการไม่เปลี่ยนรหัสแล้วถูกโจมตี
เปลี่ยน PASS_MIN_DAYS จาก 0 เป็น 2 ป้องกันการสแปมเปบี่ยนรหัส จากที่จะเปลี่ยนเมื่อไรห่ก็ได้ จะกลายเป็นเปลี่ยนได้ทุกๆ 2 วันแทน
*

sudo apt install libpam-pwquality
*libpam-pwquality : สำหรับติดตั้ง PAM (Pluggable Authentication Modules) สำหรับบังคับให้ใช้ตามที่เรา set ของรหัสทำให้มีคามแข็งแกร่งและปลอดภัย 
*

nano /etc/pam.d/common-password
*minlen=10  : ขั้นต่ำ 10ตัว
ucredit=-1  : ต้องมีตัวใหญ่อย่างน้อง1ตัว
dcredit=-1 ต้องม่ีตัวเลขอย่างน้อย 1 ตัว
lcredit=-1 ต้องมีตัวเล็กอย่างน้อย 1 ตัว
maxrepeat=3 ใส่รหัสผิดได้สูงสุด 3ครั้ง 
reject_username ไม่รับรหัสที่เป็นอันเดียวกับ username
difok=7 ถ้าเปลี่ยนรหัสใหม่แล้ว ต้องไม่เหมือนกับรหัสเก่าอย่างน้อย 7 ตัว
enforce_for_root  บังคับด้วยแม้จะเป็น root กันคนเปลี่ยนเป็น root แล้วตั้งรหัสง่ายๆ*

# Cron (time fileds)
  ┌───────────── นาที (0 - 59)
  │ ┌─────────── ชั่วโมง (0 - 23)
  │ │ ┌───────── วันที่ (1 - 31)
  │ │ │ ┌─────── เดือน (1 - 12)
  │ │ │ │ ┌───── วันในสัปดาห์ (0 - 6) (0 คือวันอาทิตย์)
  │ │ │ │ │
  * * * * * /path/to/command

# SCRIPT
# !/bin/bash
บอกว่าต้องรันด้วย /bin/bash 
bin เป็นโฟลเดอร์ที่เก็บไฟล์ปฏิบัติการพื้นฐาน และ bash เป็นชื่อโปรแกรมที่เราเรียกใช้งานให้รัน
# ARCH
arch=$(uname -a)
uname -a ไว้ปริ้นข้อมูลทั้งหมดออกมาั้ง Version ,System architec,os name และ เก็บไว้บนตัวแปร arch

**เก็บข้อความยาวๆลงตัวแปร arch**
# CPU PHYSICAL
cpuf=$(grep "physical id" /proc/cpuinfo | wc -l)
grep(Global Regular Expression Print) คือGoogle Seach ประจำ  cmd ที่ไว้ค้นหาเเล้วปริ้นผลลัพธ์ออกมา เช่น มีไฟล์อยู่ 1พันคำ ก็จะใช้ grep ในการหา (สรุปเหมือน crlt + f) ส่วนถ้าใช้ gerp -v จะกลับกันเป็นจะหาทุกคำยกเว้นคำนั้นๆ
/prco/cpuinfo เป็นไฟล์เก็บข้อมูล CPU
wc -l นับจำนวนคำและบรรทัด

**นับจำนวนคำ Physical CPU (CPU เป็นตัวๆที่เสียบอยู่บนบอร์ด)**
# CPU VIRTUAL
cpuv=$(grep "processor" /proc/cpuinfo | wc -l)
**นับจำนวนคำ Virtual CPU รวม Cores และ Threads ทั้งหมด**

# CPU VIRTUAL
cpuv=$(grep "processor" /proc/cpuinfo | wc -l)
**นับจำนวนคำ Virtual CPU รวม Cores และ Threads ทั้งหมด**
# RAM
ram_total=$(free --mega | awk '$1 == "Mem:" {print $2}')
ram_use=$(free --mega | awk '$1 == "Mem:" {print $3}')
ram_percent=$(free --mega | awk '$1 == "Mem:" {printf("%.2f"), $3/$2*100}')
free --mega ไว้ดูหน่วยเป็น Megabyte
awk กรองข้อมูลเป็นแบบตาราง
$1 == "Mem:"  เลือกเฉพาะบรรทัดที่ขึ้นต้นคำว่า Mem
$2(Total) $3(Used) ดึงค่าที่ 2และ3มาใส่
ที่เหลือก็เป็นสูตรว่า ใช้ไปเท่าไหร่ / ทั้งหมดที่มี แล้วเอาไป * 100 เพื่อหา %*

**คำนวนหาแทมทั้งหมดที่มี,แรมที่ถูกใช้ไป และคำนวณมันออกมา**
# DISK
disk_total=$(df -m | grep "/dev/" | grep -v "/boot" | awk '{disk_t += $2} END {printf ("%.1fGb\n"), disk_t/1024}')
-
df -m ดูพื้นที่ดิสก์หน่วย MB
grep "/dev/ " เอาเฉพาะ device จริงๆ
grep -v "/boot ตัด /boot ออกและไม่นับส่วนของ boot"
awkวนลูปบวกเลขพื้นที่ทั้งหมด (disk_t +=2) แล้วหาร 1024 เพื่อแปลงจาก MB เป็น GB
-
disk_use=$(df -m | grep "/dev/" | grep -v "/boot" | awk '{disk_u += $3} END {print disk_u}')
disk_percent=$(df -m | grep "/dev/" | grep -v "/boot" | awk '{disk_u += $3} {disk_t+= $2} END {printf("%d"), disk_u/disk_t*100}')

เหมือนกันเลยแค่เปลี่ยนเป็น $3 และคำนวณหา %

**หาพื้นที่ Disk ทั้งหมดเป็น GB,หาพื้นที่ ที่ใช้ไปเป็น MB,หา %การใช้ disk**
# CPU LOAD
cpul=$(vmstat 1 2 | tail -1 | awk '{printf $15}')
cpu_op=$(expr 100 - $cpul)
cpu_fin=$(printf "%.1f" $cpu_op)
vmstat 1 2 เช็กสถานะเครื่อง 2 ครั้ง ให้ห่างกัน 1 วิ
tail -1 เอาบรรทัดล่าสุด
$15 ในตารางของ vmstat ช่องที่ 15 คือ Idle (เวลาที่ CPU ว่างงาน)
 สูตร 100 - ส่วนที่ไม่ได้ใช้งาน(ทำงาน) = Load(เวลาที่ CPU ทำงาน)

**หาส่วนที่ว่างของ CPU,และแปลงเป็นส่วนที่ใช้ เช่น ว่าง 90 ก็คือ 100-90=10 แปลว่าใช้ไป 10**
# LAST BOOT
lb=$(who -b | awk '$1 == "system" {print $3 " " $4}')
who -b ไว้ดูเวลา boot ครั้งล่าสุด
awk ไว้ดึงวันที่ $3 และเวลา $4

**ดูสถานะเครื่องว่าเปิดเครื่องครั้งล่าสุดตอนไหน**

# LVM USE
lvmu=$(if [ $(lsblk | grep "lvm" | wc -l) -gt 0 ]; then echo yes; else echo no; fi)
lsblk ลิส block device ทั้งหมด
grep "lvm" หาคำว่า lvm
-gt 0ถ้าเจอบรรทัดมากกว่า ) ให้ตอบ Yes ถ้าไม่เจอให้ตอบ No

**ดูว่าเครื่องนี้เปิด LVM ใช้ได้ไหม**
# TCP CONNEXIONS
tcpc=$(ss -ta | grep ESTAB | wc -l)
ss -ta ดู Socketทั้งหมดที่เป็น TCP
grep EXTAB เอาเฉพาะสถานะ ESTABLISHED ที่เชื่อมต่ออยู่จริงๆ
wc -l ไว้นับจำนวน

**นับว่ามีการเชื่อมต่อผ่าน TCP มาาเท่าไหร่
# USER LOG
ulog=$(users | wc -w)
users โชว์ชื่อที่ user ล้อกอินอยู่
wc -w(word count) นับจำนวนคำ(คน)

**นับว่ามี User login อยู่กี่คน
# NETWORK
ip=$(hostname -I)
mac=$(ip link | grep "link/ether" | awk '{print $2}')
hostname -I ขอ IP เครื่อง
ip link ดู Networkd Interface
grep "link/ether" บรรทัดที่มี mac address  จะมีคำนี้อยู่

**ดึง Ip Addressของเครื่อง,ดึงMac Address**
# SUDO
cmnd=$(journalctl _COMM=sudo | grep COMMAND | wc -l)
journalctl _COMM =sudo ใช้ดึง log ออกจากระบบ Systemd journal (บบางทีอาจใช้ cat)
grep COMMAND นับเฉพาะบรรทัดที่มีการรันคำสั่งจริงๆ
wc -l นับบรรทัด

**ดกูว่ามีการใช้ sudo ไปแล้วกี่ครั้ง**

wall "	Architecture: $arch
	CPU physical: $cpuf
	vCPU: $cpuv
	Memory Usage: $ram_use/${ram_total}MB ($ram_percent%)
	Disk Usage: $disk_use/${disk_total} ($disk_percent%)
	CPU load: $cpu_fin%
	Last boot: $lb
	LVM use: $lvmu
	Connections TCP: $tcpc ESTABLISHED
	User log: $ulog
	Network: IP $ip ($mac)
	Sudo: $cmnd cmd"
wall คือ Write All เป็นการบังคับให้รันพวกนี้ทั้งหมด
**เอาตัวแปรทั้งหมดที่มีมาคำนวณหาแล้วจัดรูปสวยๆและประกาศเป็น Braodcast ขึ้น Terminal**

2 16
CODE FOR SETUP.md

# adduser
ใช้เพิ่มหรือเปลี่ยนแปลง user บน linux

# arch
ใช้แสดงรุ่น hardware ของเครื่อง server

# awk
ใช้ค้นหาข้อมูล text ในรูปแบบที่ซับซ้อน

# basename
ใช้แสดงเฉพาะส่วนของชื่อ filename

# bc
คำนวณตัวเลข ตามสูตรทางคณิตศาสตร์

# cal
แสดงปฏิทิน วันเดือนปี

# cat
แสดงผลข้อมูลภายใน file ในรูปแบบ text

# chgrp
เปลี่ยนเจ้าของ group ของ file

# chmod
เปลี่ยนสิทธิ์ในการเข้าถึง file

# chown
เปลี่ยนเจ้าของ file หรือ directory

# cksum
นับจำนวน bytes ของ file

# clear
ล้างหน้าจอ screen

# cmp
วิเคราะห์เปรียบเทียบ files ในระดับ bytes

# comm
วิเคราะห์เปรียบเทียบ file ที่ละบรรทัด

# cp
ทำสำเนาหรือ copy ข้อมูล

# cron
ควบคุมการเริ่มทำงานของ job schedule

# crontab
ใช้ตั้งเวลาให้คำสั่งเริ่มทำงานตามที่ต้องการ

# csplit
แตก file ตามจำนวนบรรทัด

# cut
ตัดข้อมูล file เป็น field column

# date
แสดงเวลาวันเดือนปี

# dc
เครื่องคิดเลขแบบตั้งโต๊ะ

# dd
backup ข้อมูลใน harddisk

# df
แสดงข้อมูลพื้นที่ disk ทั้งหมด

# diff
วิเคราะห์เปรียบเทียบ file ทีละบรรทัด

# dir
แสดงข้อมูล directory

# dircolors
ที่ใช้ในการปรับสีของผลลัพธ์ ls

# dirname
แสดงชื่อ directory ของ file

# du
ดูข้อมูลรายละเอียดขนาด file

# echo
ในการแสดงผลบนหน้าจอ screen

# ed
editor file ชนิดหนึ่ง

# egrep
ค้นหาบรรทัดใน file ที่ตรงเงื่อนไข

# env
สร้าง environment ในการ run program

# expand
เปลี่ยนข้อมูล file จาก tab เป็น space

# expr
ที่ใช้ประมวลผลตรรกะคณิตศาสตร์

# factor
แยกตัวประกอบทางคณิตศาสตร์

# fdisk
บริหารจัดการ disk partition

# find
ใช้ในการค้นหา file หรือ directory

# fmt
จัดเรียงข้อมูลภายใน file ในรูป format

# fold
จัดเรียงความยาวตัวอักษรแต่ละบรรทัด

# free
แสดงข้อมูลการใช้งาน memory

# fsck
ตรวจสอบและซ่อมแซม file system

# gawk
ใช้ค้นหาข้อมูล text ในรูปแบบเดียวกับ awk

# grep
ค้นหาบรรทัดใน file ที่ตรงเงื่อนไข

# groups
แสดงข้อมูล group ของ system user

# gunzip
ยกเลิกการบีบอัดข้อมูล file

# gzip
บีบอัดข้อมูล file หรือ การ zip file

# head
แสดงข้อมูลบางส่วนภายใน file

# hostname
แสดงข้อมูลชื่อของเครื่อง server

# id
แสดงข้อมูล user, group ในระบบ

# ifconfig
แสดงข้อมูลและเปลี่ยนค่า interface server

# info
ข้อมูลโปรแกรมบนระบบทั้งหมดที่ใช้งาน

# iptables
จัดการกรอง ip port ที่เข้ามาใช้งาน

# join
เชื่อมข้อมูล 2 file ด้วย field ที่เหมือนกัน

# kill
ส่ง Signal หรือยกเลิกการทำงาน process

# less
อ่านข้อมูลและค้นหาข้อมูลใน file

# ln
สร้าง link เชื่อมโยงกันระหว่าง file

# locate
ใช้ในการค้นหา file หรือ directory

# logname
แสดงชื่อ user login

# ls
แสดงข้อมูลภายใน directory

# man
แสดงคู่มือการใช้งาน program

# mkdir
สร้าง directory

# more
อ่านข้อมูลและค้นหาข้อมูลใน file

# mount
ติดตั้งใช้งานอุปกรณ์ที่เชื่อมต่อ

# mv
ย้ายตำแหน่ง file หรือ directory

# netstat
แสดงสถานะ network connection ทั้งหมด

# nice
จัดลำดับความสำคัญของ process

# nl
แสดงเลขที่บรรทัดของข้อมูลใน file

# nohup
ป้องกันการหยุดของ background process

# passwd
เปลี่ยน password ของ System user

# paste
เชื่อมข้อมูลที่ละบรรทัดจากหลาย file

# pathchk
เช็ก path ในระบบว่ามีถูกต้อง

# ping
ตรวจสอบสถานะ server ปลายทาง

# pr
แสดงข้อมูลภายใน file ในรูปแบบสิ่งพิมพ์

# printf
แสดงผลข้อมูลบนหน้าจอ screen

# ps
แสดง process ที่ทำงานใน server

# pwd
แสดง directory หรือ path ที่อยู่ปัจจุบัน

# rcp
คัดลอก file ข้ามเครื่อง server

# rm
ลบ file หรือ directory

# rmdir
ลบ directory

# rsync
sync ข้อมูล file ระหว่าง server

# screen
สร้าง session screen ขึ้นมาใหม่อีกจอ

# sdiff
วิเคราะห์เปรียบเทียบข้อมูล file ทีละบรรทัด

# sed
เปลี่ยนแปลงข้อมูล text ที่มีรูปแบบซับซ้อน

# seq
แสดงเลข sequence number

# shutdown
ปิดการทำงานของระบบ

# sleep
หน่วงเวลา

# sort
ในการจัดเรียงข้อมูล file ทีละบรรทัด

# split
แตก file ตามจำนวนบรรทัด

# su
login ด้วย user id อื่น

# sum
การตรวจสอบ checksum และ ขนาด block

# sync
เขียนข้อมูล memory ลง disk

# tac
แสดงข้อมูลใน file แบบกลับหลัง

# tail
แสดงข้อมูลบางส่วนภายใน file

# tar
จัดเก็บรวบรวม file ข้อมูล

# tee
อ่านข้อมูลพร้อมกับเขียนข้อมูลลง file

# time
จับเวลาการทำงาน process

# top
จัดเรียงอันดับแสดงการทำงานของ process

# touch
เปลี่ยนแปลง file timestamps

# tr
ค้นหาและเปลียนแปลงข้อมูล text

# traceroute
แสดงเส้นทางการทำงาน network

# tsort
จัดเรียงข้อมูลแบบ topological

# tty
แสดงชนิดของ terminal ที่ใช้งาน

# uname
แสดงชื่อระบบของ server

# unexpand
เปลี่ยน space เป็น tab

# uniq
ในการจัดเรียงข้อมูลแบบไม่ซ้ำกัน

# units
ในการแปลงค่าหน่วยวัด

# useradd
สร้าง user และจัดการ user บนระบบ

# userdel
ลบ user ออกจากระบบ

# usermod
เปลี่ยนแปลงข้อมูลของ user

# vdir
แสดงข้อมูล directory

# w
แสดง user ที่ login รวมถึงคำสั่งที่ใช้งาน

# watch
monitor process ที่ทำงานอยู่

# wc
นับจำนวนคำและบรรทัดจาก file

# whereis
ค้นหาตำแหน่ง file program

# which
ตำแหน่ง file program

# who
แสดงข้อมูล user ที่ login ขณะนั้น

# whoami
แสดงชื่อ user ที่ใช้ login

# xargs
สร้างคำสั่งใหม่จาก ouput ที่ได้ก่อนหน้า

# yes
แสดงข้อมูล text ที่ต้องการวนซ้ำไปเรื่อยๆ

# nano
ในการสร้างหรือแก้ไข file ข้อมูล text

# vi
ในการสร้างหรือแก้ไข file ข้อมูล text

# telnet
โปรโตรคอลเชื่อมต่อสื่อสารด้วยข้อมูลตัวอักษร

# ssh
เชื่อมต่อ shell server แบบเข้ารหัสความปลอดภัย

# scp
คัดลอก file ข้อมูลแบบเข้ารหัสความปลอดภัย

**NO GRAPHIC** 
ls /usr/bin/*session

LVM กับ LOGICAL FUNCTION ต่างกันยังไง

**UFW**
sudo ufw status
sudo service ufw statu



**SSH**
sudo service ssh status

**OS CHECK(DEBIAN)**
uname --kernel-version
uname -v

**GETENT USER/GROUP**
getent group sudo user42

sudo adduser name_user

sudo addgroup evaluating

sudo adduser name_user evaluating

**HOSTNAME**
hostname

**CHANGE HOSTNAME**
sudo nano /etc/hostname

sudo nano /etc/hosts

sudo reboot

hostname

**CHECK ALL PART**
lsblk

**CHECK SUDO**
which sudo

**CHECK ADD USER SUDO GROUP**
sudo adduser name_user sudo

getent group sudo

**CHECK SUDO RULES**
nano /etc/sudoers.d/sudo_config

**CHECK SUDO LOGS**
cd /var/log/sudo

cat sudo_config

**CHECK UFW ADVANCE**
dpkg -s ufw

sudo service ufw status

sudo ufw status numbered

**CHECK RULE CREATION**
suod ufw allow 8080

sudo ufw status numbered

sudo ufw delete num_rule

sudo ufw status numbered

sudo ufw delete (number)

sudo ufw status numbered

**CHECH SSH ADVANCED**
which ssh

sudo service ssh status

**CHECK SSH USAFE**
ssh root@localhost -p 2424

ssh passawuc@localhost 2424

**CHECK CRONTAB OF SCRIPT**
sudo crontab -u root -e



HelloUser42


### 🎯 เป้าหมายหลักของ Script นี้

สคริปต์นี้มีหน้าที่ **"รวบรวมข้อมูลสุขภาพของระบบ (System Health)"** แล้วทำการ **"ประกาศ (Broadcast)"** ขึ้นหน้าจอ Terminal ของทุกคนที่กำลังใช้งานอยู่ครับ

---

### 🛠️ กระบวนการทำงาน (Process)

สคริปต์ทำงานเป็น 3 ขั้นตอน:

1. **ดึงข้อมูล (Collect):** ใช้คำสั่ง Linux (เช่น `uname`, `free`, `df`) ดึงค่าดิบออกมา
    
2. **กรองและคำนวณ (Process):** ใช้ `grep`, `awk`, `expr` เพื่อตัดส่วนที่ไม่ต้องการออก และคำนวณเลข (เช่น หา %)
    
3. **แสดงผล (Display):** ใช้คำสั่ง `wall` เพื่อส่งข้อความที่จัดรูปแบบแล้วไปโชว์บนหน้าจอ
    

---

### 📊 สรุปข้อมูล 4 หมวดหมู่ที่แสดงผล

#### 1. หมวดฮาร์ดแวร์และระบบ (Hardware & System)

- **Architecture (`arch`):** ดูว่าเป็น OS อะไร รุ่นไหน (ใช้ `uname -a`)
    
- **Physical CPU (`cpuf`):** นับจำนวน CPU ตัวเป็นๆ ที่เสียบอยู่ (ใช้ `grep "physical id"`)
    
- **vCPU (`cpuv`):** นับจำนวน Core/Thread ทั้งหมด (ใช้ `grep "processor"`)
    
- **Last Boot (`lb`):** เครื่องเปิดมาเมื่อไหร่ (ใช้ `who -b`)
    
- **LVM Use (`lvmu`):** มีการใช้ LVM ไหม (เช็กด้วย `lsblk`)
    

#### 2. หมวดทรัพยากรเครื่อง (Resources Usage)

- **Memory (`ram`):** แรมใช้ไปเท่าไหร่/ทั้งหมดเท่าไหร่ และคิดเป็นกี่ % (ใช้ `free`)
    
- **Disk (`disk`):** พื้นที่เก็บข้อมูลใช้ไปเท่าไหร่ (ใช้ `df`) **จุดเด่น:** ตัดพาร์ทิชัน `/boot` ออก ไม่เอามานับ
    
- **CPU Load (`cpu_fin`):** CPU ทำงานหนักแค่ไหน (ใช้ `vmstat` เอา 100 ลบด้วยค่าความว่าง)
    

#### 3. หมวดเครือข่าย (Network)

- **IP & MAC (`ip`, `mac`):** ที่อยู่ของเครื่องในวงแลน และรหัสการ์ดแลน
    
- **TCP Connections (`tcpc`):** มีการเชื่อมต่อเข้ามาค้างอยู่กี่รายการ (ใช้ `ss -ta`)
    

#### 4. หมวดผู้ใช้งาน (Users & Admin)

- **User Log (`ulog`):** มีคนล็อกอินอยู่กี่คน (ใช้ `users`)
    
- **Sudo (`cmnd`):** มีการใช้คำสั่งผ่าน Sudo ไปแล้วกี่ครั้ง (เช็ก Log ด้วย `journalctl` หรือดูไฟล์ log)
    

---

### 🔑 คีย์เวิร์ดคำสั่งที่ใช้บ่อยในนี้ (ต้องตอบได้!)

- **`grep`**: ค้นหา/กรองคำ
    
- **`awk`**: ดึงข้อมูลเฉพาะคอลัมน์ที่อยากได้
    
- **`wc`**: นับจำนวน (บรรทัด/คำ)
    
- **`wall`**: ตะโกนข้อความใส่หน้าจอทุกคน (Write All)
    

### 💡 เกร็ดเพิ่มเติม (Context)

ปกติสคริปต์นี้จะไม่ได้รันด้วยมือครับ แต่จะถูกสั่งให้รันอัตโนมัติโดย **Cron (Crontab)** (เช่น ทุกๆ 10 นาที) เพื่อให้ Admin เห็นสถานะเครื่องตลอดเวลาครับ


ไฟร์วอลล์ (Firewall) คือ ==ระบบรักษาความปลอดภัยเครือข่าย ทำหน้าที่เป็น "กำแพง" คอยตรวจสอบและกรองข้อมูลที่เข้าออกระหว่างเครือข่ายภายในที่น่าเชื่อถือกับเครือข่ายภายนอกที่ไม่น่าเชื่อถือ== (เช่น อินเทอร์เน็ต) โดยอิงจากกฎที่กำหนดไว้ล่วงหน้า เพื่อป้องกันการเข้าถึงโดยไม่ได้รับอนุญาต การโจมตีทางไซเบอร์ และมัลแวร์ต่างๆ. 

หน้าที่หลักของไฟร์วอลล์

- **กรองข้อมูล (Filtering):** ตรวจสอบแพ็กเก็ตข้อมูลขาเข้า-ขาออก และตัดสินใจว่าจะอนุญาตให้ผ่านหรือไม่ตามกฎที่ตั้งไว้.
- **ป้องกันภัยคุกคาม:** กั้นการเข้าถึงที่ไม่ได้รับอนุญาต, ไวรัส, สแปม, และกิจกรรมที่เป็นอันตรายอื่นๆ.
- **ควบคุมการเข้าถึง:** กำหนดได้ว่าใครสามารถเข้าถึงข้อมูลส่วนไหนได้ เพื่อรักษาความปลอดภัยและการจัดการข้อมูลที่มีประสิทธิภาพ. 

ไฟร์วอลล์มีกี่ประเภท

ไฟร์วอลล์มีทั้งแบบฮาร์ดแวร์ (ติดตั้งในอุปกรณ์) และซอฟต์แวร์ (ติดตั้งบนคอมพิวเตอร์). - **[Hardware Firewall](https://www.google.com/search?q=Hardware+Firewall&oq=firewall+%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3&gs_lcrp=EgZjaHJvbWUqBwgAEAAYgAQyBwgAEAAYgAQyBwgBEAAYgAQyBwgCEAAYgAQyBwgDEAAYgAQyBwgEEAAY7wUyBwgFEAAY7wUyBwgGEAAY7wXSAQg5NjMxajFqOagCALACAA&sourceid=chrome&ie=UTF-8&ved=2ahUKEwj39c3-ldaRAxV6UvUHHUVPB4UQgK4QegYIAQgAEBM):** อุปกรณ์จริงที่ติดตั้งตามขอบเครือข่าย เช่น ในเราเตอร์ (Router) เหมาะสำหรับองค์กร.
- **[Software Firewall](https://www.google.com/search?q=Software+Firewall&oq=firewall+%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3&gs_lcrp=EgZjaHJvbWUqBwgAEAAYgAQyBwgAEAAYgAQyBwgBEAAYgAQyBwgCEAAYgAQyBwgDEAAYgAQyBwgEEAAY7wUyBwgFEAAY7wUyBwgGEAAY7wXSAQg5NjMxajFqOagCALACAA&sourceid=chrome&ie=UTF-8&ved=2ahUKEwj39c3-ldaRAxV6UvUHHUVPB4UQgK4QegYIAQgAEBU):** โปรแกรมที่ติดตั้งบนคอมพิวเตอร์แต่ละเครื่อง ทำหน้าที่ป้องกันอุปกรณ์นั้นๆ โดยตรง (เช่น Windows Firewall).
- **[Cloud/Virtual Firewall](https://www.google.com/search?q=Cloud%2FVirtual+Firewall&oq=firewall+%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3&gs_lcrp=EgZjaHJvbWUqBwgAEAAYgAQyBwgAEAAYgAQyBwgBEAAYgAQyBwgCEAAYgAQyBwgDEAAYgAQyBwgEEAAY7wUyBwgFEAAY7wUyBwgGEAAY7wXSAQg5NjMxajFqOagCALACAA&sourceid=chrome&ie=UTF-8&ved=2ahUKEwj39c3-ldaRAxV6UvUHHUVPB4UQgK4QegYIAQgAEBc):** เป็นบริการบนคลาวด์ หรือทำงานในรูปแบบเสมือน. 

ทำไมไฟร์วอลล์ถึงสำคัญ?

เพราะอินเทอร์เน็ตมีความเสี่ยงสูง ไฟร์วอลล์จึงเป็นเหมือนยามเฝ้าประตูที่ช่วยให้การสื่อสารบนเครือข่ายปลอดภัย ปกป้องข้อมูลสำคัญ และทำให้การใช้งานอินเทอร์เน็ตเป็นไปอย่างราบรื่นและปลอดภัยยิ่งขึ้น.

SSH
SSH (Secure Shell) คือ==โปรโตคอลเครือข่ายที่เข้ารหัสข้อมูลเพื่อการสื่อสารที่ปลอดภัยระหว่างคอมพิวเตอร์สองเครื่อง== ทำให้ผู้ใช้สามารถเข้าสู่ระบบและควบคุมเซิร์ฟเวอร์หรืออุปกรณ์ระยะไกลได้อย่างปลอดภัยผ่านอินเทอร์เน็ต โดยเข้ารหัสทุกอย่างตั้งแต่รหัสผ่านไปจนถึงคำสั่ง ช่วยป้องกันการดักฟังหรือขโมยข้อมูล ซึ่งเป็นทางเลือกที่ปลอดภัยกว่าโปรโตคอลเก่าอย่าง Telnet. 

SSH ทำงานอย่างไร:

- **[การเข้ารหัส (Encryption)](https://www.google.com/search?q=%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%80%E0%B8%82%E0%B9%89%E0%B8%B2%E0%B8%A3%E0%B8%AB%E0%B8%B1%E0%B8%AA+%28Encryption%29&sca_esv=4cac260d7adc13d6&sxsrf=AE3TifPCyN36ti3YVl0PCGO9SqkQy4HMsg%3A1766577491120&ei=U9VLabeAB_qk1e8PxZ6dqAg&ved=2ahUKEwj7yaOJltaRAxXIaPUHHe6BIWIQgK4QegYIAQgAEAk&uact=5&oq=SSH+%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3&gs_lp=Egxnd3Mtd2l6LXNlcnAaAhgCIhlTU0gg4LiE4Li34Lit4Lit4Liw4LmE4LijMgoQIxiABBgnGIoFMgYQABgWGB4yCBAAGBYYChgeMggQABiABBiiBDIFEAAY7wUyBRAAGO8FSPJ5UPNkWNt3cAt4AZABAJgBY6ABkweqAQIxMbgBA8gBAPgBAZgCFqAC0gfCAgoQABiwAxjWBBhHwgIEECMYJ8ICCxAAGIAEGLEDGIMBwgIREC4YgAQYsQMY0QMYgwEYxwHCAg4QABiABBixAxiDARiKBcICDRAAGIAEGEMYigUYiwPCAgsQABiABBixAxiLA8ICFxAuGIAEGLEDGNEDGNIDGMcBGKgDGIsDwgIIEAAYgAQYiwPCAgoQABiABBhDGIoFwgIFEAAYgASYAwCIBgGQBgiSBwQyMS4xoAfyP7IHBDEwLjG4B7MHwgcGMC4xOC40yAcwgAgA&sclient=gws-wiz-serp)**: สร้างช่องทางการสื่อสารที่เข้ารหัส ทำให้ข้อมูลที่ส่งไปมาอ่านไม่ออกสำหรับบุคคลที่สาม.
- **[การพิสูจน์ตัวตน (Authentication)](https://www.google.com/search?q=%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B8%9E%E0%B8%B4%E0%B8%AA%E0%B8%B9%E0%B8%88%E0%B8%99%E0%B9%8C%E0%B8%95%E0%B8%B1%E0%B8%A7%E0%B8%95%E0%B8%99+%28Authentication%29&sca_esv=4cac260d7adc13d6&sxsrf=AE3TifPCyN36ti3YVl0PCGO9SqkQy4HMsg%3A1766577491120&ei=U9VLabeAB_qk1e8PxZ6dqAg&ved=2ahUKEwj7yaOJltaRAxXIaPUHHe6BIWIQgK4QegYIAQgAEAs&uact=5&oq=SSH+%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3&gs_lp=Egxnd3Mtd2l6LXNlcnAaAhgCIhlTU0gg4LiE4Li34Lit4Lit4Liw4LmE4LijMgoQIxiABBgnGIoFMgYQABgWGB4yCBAAGBYYChgeMggQABiABBiiBDIFEAAY7wUyBRAAGO8FSPJ5UPNkWNt3cAt4AZABAJgBY6ABkweqAQIxMbgBA8gBAPgBAZgCFqAC0gfCAgoQABiwAxjWBBhHwgIEECMYJ8ICCxAAGIAEGLEDGIMBwgIREC4YgAQYsQMY0QMYgwEYxwHCAg4QABiABBixAxiDARiKBcICDRAAGIAEGEMYigUYiwPCAgsQABiABBixAxiLA8ICFxAuGIAEGLEDGNEDGNIDGMcBGKgDGIsDwgIIEAAYgAQYiwPCAgoQABiABBhDGIoFwgIFEAAYgASYAwCIBgGQBgiSBwQyMS4xoAfyP7IHBDEwLjG4B7MHwgcGMC4xOC40yAcwgAgA&sclient=gws-wiz-serp)**: ใช้ระบบคีย์ (Public Key/Private Key) หรือรหัสผ่าน เพื่อยืนยันตัวตนของผู้ใช้และเซิร์ฟเวอร์ เพื่อให้มั่นใจว่ากำลังสื่อสารกับเครื่องที่ถูกต้อง.
- **[สถาปัตยกรรม Client-Server](https://www.google.com/search?q=%E0%B8%AA%E0%B8%96%E0%B8%B2%E0%B8%9B%E0%B8%B1%E0%B8%95%E0%B8%A2%E0%B8%81%E0%B8%A3%E0%B8%A3%E0%B8%A1+Client-Server&sca_esv=4cac260d7adc13d6&sxsrf=AE3TifPCyN36ti3YVl0PCGO9SqkQy4HMsg%3A1766577491120&ei=U9VLabeAB_qk1e8PxZ6dqAg&ved=2ahUKEwj7yaOJltaRAxXIaPUHHe6BIWIQgK4QegYIAQgAEA0&uact=5&oq=SSH+%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3&gs_lp=Egxnd3Mtd2l6LXNlcnAaAhgCIhlTU0gg4LiE4Li34Lit4Lit4Liw4LmE4LijMgoQIxiABBgnGIoFMgYQABgWGB4yCBAAGBYYChgeMggQABiABBiiBDIFEAAY7wUyBRAAGO8FSPJ5UPNkWNt3cAt4AZABAJgBY6ABkweqAQIxMbgBA8gBAPgBAZgCFqAC0gfCAgoQABiwAxjWBBhHwgIEECMYJ8ICCxAAGIAEGLEDGIMBwgIREC4YgAQYsQMY0QMYgwEYxwHCAg4QABiABBixAxiDARiKBcICDRAAGIAEGEMYigUYiwPCAgsQABiABBixAxiLA8ICFxAuGIAEGLEDGNEDGNIDGMcBGKgDGIsDwgIIEAAYgAQYiwPCAgoQABiABBhDGIoFwgIFEAAYgASYAwCIBgGQBgiSBwQyMS4xoAfyP7IHBDEwLjG4B7MHwgcGMC4xOC40yAcwgAgA&sclient=gws-wiz-serp)**: เครื่องผู้ใช้ (Client) เชื่อมต่อกับเครื่องเซิร์ฟเวอร์ (Server) เพื่อส่งคำสั่งและรับผลลัพธ์. 

ประโยชน์หลักของ SSH:

- **[การจัดการระยะไกลที่ปลอดภัย](https://www.google.com/search?q=%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B8%88%E0%B8%B1%E0%B8%94%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B8%A3%E0%B8%B0%E0%B8%A2%E0%B8%B0%E0%B9%84%E0%B8%81%E0%B8%A5%E0%B8%97%E0%B8%B5%E0%B9%88%E0%B8%9B%E0%B8%A5%E0%B8%AD%E0%B8%94%E0%B8%A0%E0%B8%B1%E0%B8%A2&sca_esv=4cac260d7adc13d6&sxsrf=AE3TifPCyN36ti3YVl0PCGO9SqkQy4HMsg%3A1766577491120&ei=U9VLabeAB_qk1e8PxZ6dqAg&ved=2ahUKEwj7yaOJltaRAxXIaPUHHe6BIWIQgK4QegYIAQgAEBM&uact=5&oq=SSH+%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3&gs_lp=Egxnd3Mtd2l6LXNlcnAaAhgCIhlTU0gg4LiE4Li34Lit4Lit4Liw4LmE4LijMgoQIxiABBgnGIoFMgYQABgWGB4yCBAAGBYYChgeMggQABiABBiiBDIFEAAY7wUyBRAAGO8FSPJ5UPNkWNt3cAt4AZABAJgBY6ABkweqAQIxMbgBA8gBAPgBAZgCFqAC0gfCAgoQABiwAxjWBBhHwgIEECMYJ8ICCxAAGIAEGLEDGIMBwgIREC4YgAQYsQMY0QMYgwEYxwHCAg4QABiABBixAxiDARiKBcICDRAAGIAEGEMYigUYiwPCAgsQABiABBixAxiLA8ICFxAuGIAEGLEDGNEDGNIDGMcBGKgDGIsDwgIIEAAYgAQYiwPCAgoQABiABBhDGIoFwgIFEAAYgASYAwCIBgGQBgiSBwQyMS4xoAfyP7IHBDEwLjG4B7MHwgcGMC4xOC40yAcwgAgA&sclient=gws-wiz-serp)**: เข้าถึงและจัดการเซิร์ฟเวอร์ Linux/Unix, เราเตอร์, หรืออุปกรณ์เครือข่ายได้อย่างปลอดภัย.
- **[การถ่ายโอนไฟล์ที่ปลอดภัย (SFTP)](https://www.google.com/search?q=%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B8%96%E0%B9%88%E0%B8%B2%E0%B8%A2%E0%B9%82%E0%B8%AD%E0%B8%99%E0%B9%84%E0%B8%9F%E0%B8%A5%E0%B9%8C%E0%B8%97%E0%B8%B5%E0%B9%88%E0%B8%9B%E0%B8%A5%E0%B8%AD%E0%B8%94%E0%B8%A0%E0%B8%B1%E0%B8%A2+%28SFTP%29&sca_esv=4cac260d7adc13d6&sxsrf=AE3TifPCyN36ti3YVl0PCGO9SqkQy4HMsg%3A1766577491120&ei=U9VLabeAB_qk1e8PxZ6dqAg&ved=2ahUKEwj7yaOJltaRAxXIaPUHHe6BIWIQgK4QegYIAQgAEBU&uact=5&oq=SSH+%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3&gs_lp=Egxnd3Mtd2l6LXNlcnAaAhgCIhlTU0gg4LiE4Li34Lit4Lit4Liw4LmE4LijMgoQIxiABBgnGIoFMgYQABgWGB4yCBAAGBYYChgeMggQABiABBiiBDIFEAAY7wUyBRAAGO8FSPJ5UPNkWNt3cAt4AZABAJgBY6ABkweqAQIxMbgBA8gBAPgBAZgCFqAC0gfCAgoQABiwAxjWBBhHwgIEECMYJ8ICCxAAGIAEGLEDGIMBwgIREC4YgAQYsQMY0QMYgwEYxwHCAg4QABiABBixAxiDARiKBcICDRAAGIAEGEMYigUYiwPCAgsQABiABBixAxiLA8ICFxAuGIAEGLEDGNEDGNIDGMcBGKgDGIsDwgIIEAAYgAQYiwPCAgoQABiABBhDGIoFwgIFEAAYgASYAwCIBgGQBgiSBwQyMS4xoAfyP7IHBDEwLjG4B7MHwgcGMC4xOC40yAcwgAgA&sclient=gws-wiz-serp)**: ถ่ายโอนไฟล์ระหว่างเครื่องได้อย่างปลอดภัยโดยใช้โปรโตคอลที่เข้ารหัส.
- **[การรันคำสั่งระยะไกล](https://www.google.com/search?q=%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B8%A3%E0%B8%B1%E0%B8%99%E0%B8%84%E0%B8%B3%E0%B8%AA%E0%B8%B1%E0%B9%88%E0%B8%87%E0%B8%A3%E0%B8%B0%E0%B8%A2%E0%B8%B0%E0%B9%84%E0%B8%81%E0%B8%A5&sca_esv=4cac260d7adc13d6&sxsrf=AE3TifPCyN36ti3YVl0PCGO9SqkQy4HMsg%3A1766577491120&ei=U9VLabeAB_qk1e8PxZ6dqAg&ved=2ahUKEwj7yaOJltaRAxXIaPUHHe6BIWIQgK4QegYIAQgAEBc&uact=5&oq=SSH+%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3&gs_lp=Egxnd3Mtd2l6LXNlcnAaAhgCIhlTU0gg4LiE4Li34Lit4Lit4Liw4LmE4LijMgoQIxiABBgnGIoFMgYQABgWGB4yCBAAGBYYChgeMggQABiABBiiBDIFEAAY7wUyBRAAGO8FSPJ5UPNkWNt3cAt4AZABAJgBY6ABkweqAQIxMbgBA8gBAPgBAZgCFqAC0gfCAgoQABiwAxjWBBhHwgIEECMYJ8ICCxAAGIAEGLEDGIMBwgIREC4YgAQYsQMY0QMYgwEYxwHCAg4QABiABBixAxiDARiKBcICDRAAGIAEGEMYigUYiwPCAgsQABiABBixAxiLA8ICFxAuGIAEGLEDGNEDGNIDGMcBGKgDGIsDwgIIEAAYgAQYiwPCAgoQABiABBhDGIoFwgIFEAAYgASYAwCIBgGQBgiSBwQyMS4xoAfyP7IHBDEwLjG4B7MHwgcGMC4xOC40yAcwgAgA&sclient=gws-wiz-serp)**: สามารถสั่งรันคำสั่งบนเครื่องอื่นได้จากเครื่องของเราเอง.
- **[ทางเลือกที่ปลอดภัย](https://www.google.com/search?q=%E0%B8%97%E0%B8%B2%E0%B8%87%E0%B9%80%E0%B8%A5%E0%B8%B7%E0%B8%AD%E0%B8%81%E0%B8%97%E0%B8%B5%E0%B9%88%E0%B8%9B%E0%B8%A5%E0%B8%AD%E0%B8%94%E0%B8%A0%E0%B8%B1%E0%B8%A2&sca_esv=4cac260d7adc13d6&sxsrf=AE3TifPCyN36ti3YVl0PCGO9SqkQy4HMsg%3A1766577491120&ei=U9VLabeAB_qk1e8PxZ6dqAg&ved=2ahUKEwj7yaOJltaRAxXIaPUHHe6BIWIQgK4QegYIAQgAEBk&uact=5&oq=SSH+%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3&gs_lp=Egxnd3Mtd2l6LXNlcnAaAhgCIhlTU0gg4LiE4Li34Lit4Lit4Liw4LmE4LijMgoQIxiABBgnGIoFMgYQABgWGB4yCBAAGBYYChgeMggQABiABBiiBDIFEAAY7wUyBRAAGO8FSPJ5UPNkWNt3cAt4AZABAJgBY6ABkweqAQIxMbgBA8gBAPgBAZgCFqAC0gfCAgoQABiwAxjWBBhHwgIEECMYJ8ICCxAAGIAEGLEDGIMBwgIREC4YgAQYsQMY0QMYgwEYxwHCAg4QABiABBixAxiDARiKBcICDRAAGIAEGEMYigUYiwPCAgsQABiABBixAxiLA8ICFxAuGIAEGLEDGNEDGNIDGMcBGKgDGIsDwgIIEAAYgAQYiwPCAgoQABiABBhDGIoFwgIFEAAYgASYAwCIBgGQBgiSBwQyMS4xoAfyP7IHBDEwLjG4B7MHwgcGMC4xOC40yAcwgAgA&sclient=gws-wiz-serp)**: แทนที่โปรโตคอลเดิมที่ไม่เข้ารหัส เช่น Telnet และ FTP. 

การใช้งาน:

- ใช้โปรแกรม SSH Client (เช่น PuTTY, OpenSSH) เชื่อมต่อกับเซิร์ฟเวอร์โดยระบุ IP Address หรือ Hostname และพอร์ต (ค่าเริ่มต้นคือ 22).
- เมื่อเชื่อมต่อสำเร็จ จะเห็นหน้าจอ Command Line เหมือนกับที่นั่งอยู่หน้าเครื่องเซิร์ฟเวอร์นั้นๆ.



APT
ในบริบทของระบบปฏิบัติการ (OS) **APT (Advanced Package Tool)** คือเครื่องมือจัดการแพ็กเกจสำหรับระบบปฏิบัติการ Linux ตระกูล Debian (เช่น Ubuntu, Mint) ใช้สำหรับติดตั้ง อัปเดต ลบซอฟต์แวร์ และจัดการการพึ่งพาของแพ็กเกจ ทำให้การจัดการโปรแกรมใน Linux ง่ายขึ้นมาก มีคำสั่งหลักๆ เช่น `apt install`, `apt update`, `apt upgrade` และคำสั่งที่ใหม่กว่าอย่าง `apt` (แทน `apt-get`) ที่ใช้งานง่ายกว่า. 

APT คืออะไร (ใน OS)

- **Advanced Package Tool (APT)**: ชื่อเต็มของ APT เป็นระบบที่ช่วยจัดการซอฟต์แวร์บน Linux.
- **หน้าที่หลัก**: ทำให้การติดตั้ง การอัปเดต และการลบโปรแกรมบนระบบ Linux เป็นไปโดยอัตโนมัติ.
- **ทำงานกับอะไร**: ทำงานร่วมกับระบบแพ็กเกจพื้นฐานอย่าง `dpkg` เพื่อจัดการความสัมพันธ์ระหว่างแพ็กเกจต่างๆ.
- **คำสั่งที่ใช้**:
    - `sudo apt update`: ดึงรายการแพ็กเกจที่อัปเดตใหม่จากที่เก็บ.
    - `sudo apt install <package>`: ติดตั้งซอฟต์แวร์.
    - `sudo apt upgrade`: อัปเกรดแพ็กเกจที่ติดตั้งไว้.
    - `apt` (ใหม่) เทียบกับ `apt-get` (เก่า): คำสั่ง `apt` เป็นเวอร์ชันที่ทันสมัยกว่า ใช้งานง่ายกว่า และมีข้อความที่อ่านง่ายกว่า `apt-get` โดยรวมแล้วแนะนำให้ใช้ `apt` มากกว่า. 

ตัวอย่างคำสั่งที่ใช้งานบ่อย

- **อัปเดตรายการแพ็กเกจ**: `sudo apt update`.
- **อัปเกรดระบบ**: `sudo apt upgrade`.
- **ติดตั้งโปรแกรม (เช่น Firefox)**: `sudo apt install firefox`.
- **ลบโปรแกรม (ลบไฟล์โปรแกรมออก)**: `sudo apt remove firefox`.
- **ลบโปรแกรมพร้อมไฟล์ตั้งค่า**: `sudo apt purge firefox`.
- **ค้นหาโปรแกรม**: `apt search <keyword>`.



APLITUDE
**Aptitude (แอptิ-จูด)** ในบริบทของระบบปฏิบัติการ (OS) หรือโดยทั่วไป หมายถึง **ความถนัด, ความสามารถเฉพาะทาง, หรือศักยภาพในการเรียนรู้และทำงานบางอย่างได้ดีเป็นพิเศษ** โดยไม่ได้วัดจากความรู้ที่เคยมี แต่เป็นการทดสอบ "สิ่งที่ทำได้ดีโดยธรรมชาติ" หรือความสามารถในการคิดวิเคราะห์ การแก้ปัญหา หรือการปรับตัว ซึ่งต่างจาก Attitude (ทัศนคติ) และมักใช้ในการคัดเลือกบุคลากรเพื่อดูความเหมาะสมกับงาน. 

**ความหมายหลักๆ ของ Aptitude:**

- **ความถนัดโดยธรรมชาติ (Natural Ability):** ศักยภาพที่มีมาแต่กำเนิดในการทำกิจกรรมบางอย่าง ไม่ว่าจะเป็นด้านร่างกายหรือจิตใจ.
- **ความสามารถในการเรียนรู้ (Learning Capacity):** ความฉลาดในการเรียนรู้สิ่งใหม่ๆ ได้อย่างรวดเร็ว.
- **ศักยภาพในการประสบความสำเร็จ (Potential for Success):** การทำนายว่าบุคคลจะทำได้ดีในงานหรือสาขาใดสาขาหนึ่งในอนาคต. 

**การนำไปใช้ (Aptitude Test):**

- **การจ้างงาน:** ใช้ทดสอบผู้สมัครงานว่ามีทักษะและความสามารถที่จำเป็นต่อตำแหน่งนั้นๆ หรือไม่ เช่น การคิดวิเคราะห์ การแก้ปัญหาเฉพาะหน้า.
- **การศึกษา:** ใช้จำแนกผู้เรียนว่าถนัดเรียนด้านไหน ช่วยในการเลือกสาขาวิชาหรืออาชีพที่เหมาะสม. 

**ตัวอย่างการทดสอบความถนัด:**

- **การคิดเชิงตรรกะ (Logical Reasoning):** ทดสอบการแก้ปัญหาและวิเคราะห์ข้อมูล.
- **การตีความข้อมูล (Data Interpretation):** วัดความเข้าใจและจัดการข้อมูลใหม่.
- **ความสามารถทางกลไก (Mechanical Aptitude):** วัดความเข้าใจเกี่ยวกับเครื่องมือหรือระบบเครื่องยนต์. 

สรุปคือ Aptitude บอกเราว่าคุณมีแนวโน้มที่จะทำอะไรได้ดีโดยธรรมชาติ ไม่ใช่สิ่งที่คุณเรียนรู้มาแล้วเท่านั้น.




SCRIPT
นี่คือ **สรุปจบในหน้าเดียว** สำหรับสคริปต์ `monitoring.sh` ครับ เอาไว้จำภาพรวมไปตอบกรรมการได้เลยครับ

---

### 🎯 เป้าหมายหลักของ Script นี้

สคริปต์นี้มีหน้าที่ **"รวบรวมข้อมูลสุขภาพของระบบ (System Health)"** แล้วทำการ **"ประกาศ (Broadcast)"** ขึ้นหน้าจอ Terminal ของทุกคนที่กำลังใช้งานอยู่ครับ

---

### 🛠️ กระบวนการทำงาน (Process)

สคริปต์ทำงานเป็น 3 ขั้นตอน:

1. **ดึงข้อมูล (Collect):** ใช้คำสั่ง Linux (เช่น `uname`, `free`, `df`) ดึงค่าดิบออกมา
    
2. **กรองและคำนวณ (Process):** ใช้ `grep`, `awk`, `expr` เพื่อตัดส่วนที่ไม่ต้องการออก และคำนวณเลข (เช่น หา %)
    
3. **แสดงผล (Display):** ใช้คำสั่ง `wall` เพื่อส่งข้อความที่จัดรูปแบบแล้วไปโชว์บนหน้าจอ
    

---

### 📊 สรุปข้อมูล 4 หมวดหมู่ที่แสดงผล

#### 1. หมวดฮาร์ดแวร์และระบบ (Hardware & System)

- **Architecture (`arch`):** ดูว่าเป็น OS อะไร รุ่นไหน (ใช้ `uname -a`)
    
- **Physical CPU (`cpuf`):** นับจำนวน CPU ตัวเป็นๆ ที่เสียบอยู่ (ใช้ `grep "physical id"`)
    
- **vCPU (`cpuv`):** นับจำนวน Core/Thread ทั้งหมด (ใช้ `grep "processor"`)
    
- **Last Boot (`lb`):** เครื่องเปิดมาเมื่อไหร่ (ใช้ `who -b`)
    
- **LVM Use (`lvmu`):** มีการใช้ LVM ไหม (เช็กด้วย `lsblk`)
    

#### 2. หมวดทรัพยากรเครื่อง (Resources Usage)

- **Memory (`ram`):** แรมใช้ไปเท่าไหร่/ทั้งหมดเท่าไหร่ และคิดเป็นกี่ % (ใช้ `free`)
    
- **Disk (`disk`):** พื้นที่เก็บข้อมูลใช้ไปเท่าไหร่ (ใช้ `df`) **จุดเด่น:** ตัดพาร์ทิชัน `/boot` ออก ไม่เอามานับ
    
- **CPU Load (`cpu_fin`):** CPU ทำงานหนักแค่ไหน (ใช้ `vmstat` เอา 100 ลบด้วยค่าความว่าง)
    

#### 3. หมวดเครือข่าย (Network)

- **IP & MAC (`ip`, `mac`):** ที่อยู่ของเครื่องในวงแลน และรหัสการ์ดแลน
    
- **TCP Connections (`tcpc`):** มีการเชื่อมต่อเข้ามาค้างอยู่กี่รายการ (ใช้ `ss -ta`)
    

#### 4. หมวดผู้ใช้งาน (Users & Admin)

- **User Log (`ulog`):** มีคนล็อกอินอยู่กี่คน (ใช้ `users`)
    
- **Sudo (`cmnd`):** มีการใช้คำสั่งผ่าน Sudo ไปแล้วกี่ครั้ง (เช็ก Log ด้วย `journalctl` หรือดูไฟล์ log)
    

---

### 🔑 คีย์เวิร์ดคำสั่งที่ใช้บ่อยในนี้ (ต้องตอบได้!)

- **`grep`**: ค้นหา/กรองคำ
    
- **`awk`**: ดึงข้อมูลเฉพาะคอลัมน์ที่อยากได้
    
- **`wc`**: นับจำนวน (บรรทัด/คำ)
    
- **`wall`**: ตะโกนข้อความใส่หน้าจอทุกคน (Write All)
    

### 💡 เกร็ดเพิ่มเติม (Context)

ปกติสคริปต์นี้จะไม่ได้รันด้วยมือครับ แต่จะถูกสั่งให้รันอัตโนมัติโดย **Cron (Crontab)** (เช่น ทุกๆ 10 นาที) เพื่อให้ Admin เห็นสถานะเครื่องตลอดเวลาครับ


