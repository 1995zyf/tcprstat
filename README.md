
/*


install:
yum install perf
yum -y install bison yacc
yum -y install flex
yum install patch
yum install glibc-static

install autoreconf




������ʱ��ͳ�ƹ��ߣ�����ʱ����ֵͳ�ƣ���¼������ֵ�İ��������������ݰ�ʱ�����¼����־�ļ����������Ը���ʱ������ٶ�λ��ץ���ļ������в��������á�
ͳ����Ϣ:
timestamp:ʱ��� 
count:������ 
max:���ʱ�� 
min:��Сʱ�� 
avg:ƽ��ʱ�� 
med:����ʱ�Ӵ�С�����������м��ʱ��ֵ������100���������50������ʱ��Ϊ���� 
stddev:ÿ������ʱ��ƽ��֮�͵�ƽ��ֵ����avg
��ƽ���Ĳ�ֵ����ֵ���Է�ӳʱ�Ӳ������ 

tc:ʱ�ӳ���40ms�İ�����������ͨ��-T����ָ�����ʱ�� 
95_max:����ʱ�Ӵ�С�������򣬵�95%��ʱ��ֵ������1000
�����󣬰����ǵ�ʱ��ֵ���򣬵�%95��ʱ��Ҳ���ǵ�950�������Ա��ʱ��ֵ 

95_avg: ����ʱ�Ӵ�С��������ʱ��ֵС��95%ʱ�ӵ�ƽ��ֵ 
95_std:����ʱ�Ӵ�С��������ʱ��ֵС��95%��stddevֵ 
99_max:����ʱ�Ӵ�С�������򣬵�95%��ʱ��ֵ������1000
�����󣬰����ǵ�ʱ��ֵ���򣬵�%95��ʱ��Ҳ���ǵ�990�������Ա��ʱ��ֵ 

99_avg:����ʱ�Ӵ�С��������ʱ��ֵС��99%ʱ�ӵ�ƽ��ֵ
99_std:����ʱ�Ӵ�С��������ʱ��ֵС��99%��stddevֵ



�����в���:
-p:�˿�
-l:ip
-o:��ӡʱ�ӳ���-T����ָ���İ�������
-T:ʱ��ͳ����ֵ��������ʱ��Ļ�ͨ��tc��ӡ������ʱ����ֵ�İ�����
-o:����а���ʱ�ӳ�����ֵ����Ѹð���ʱ�����¼�����ļ��У��������԰�����������
-t:ͳ�ƴ�ӡʱ����
-n:����ӡ��ô���
-r:����ͳ�ƹ��ܵ�ץ���ļ�



ʹ�÷���:

ץ���ļ����߷���:tcprstat -p 1111 -l 10.2.x.x -t 1 -n 333333 -r xxx.pcap -T 10 -o 
timetamp.txt

���߷���:tcprstat -p 1111 -l 10.2.x.x -t 1 -n 333333 





����˵��:  ����pthread�߳̾�̬��
����tcprstat

��RHEL6.1(Red Hat Enterprise Linux Server)�Ͼ�̬���벢�����ס�tcprstat
����Ҳ��������⡣


Դ�����أ�tcprstat@Launchpad ���bzr branch lp:tcprstat

�������./bootstrap && ./configure && make

���˳���Ļ����ͽ����ˡ��������ҵķ��а�ᱨ���´���

gcc -Wall -Werror -g -pthread -I../libpcap/libpcap-1.1.1/ -g -O2 -static -L../
libpcap/libpcap-1.1.1/ \

-o tcprstat-static tcprstat_static-tcprstat.o tcprstat_static-functions.o 
tcprstat_static-capture.o \

tcprstat_static-process-packet.o tcprstat_static-local-addresses.o 
tcprstat_static-stats.o \

tcprstat_static-output.o tcprstat_static-stats-hash.o -lpthread -lpcap -L/usr/
lib64/

ld: cannot find -lpthread
collect2: ld returned 1 exit status
��������ͬѧָ�㣬�����ڳ��Ծ�̬����ʱ(-static)���Ҳ���pthread�����ӿ⡣
pthread��Linux��glibc����ʵ��(NPTL)��������Ҫ��̬�������ӣ�����Ҫ��Ӧ��glibc
��̬���ӿ⡣


��ѯ��̨������Ӧ��glibc�汾Ϊglibc-2.12-1.25.el6.x86_64(rpm -qa|grep glibc)
����ôҲ��Ҫ��Ӧ�汾�ľ�̬���ӿ⣬������������Ӧ��rpm��������װ��


glibc-static-2.12-1.25.el6.x86_64.rpm
rpm -ivh glibc-static-2.12-1.25.el6.x86_64.rpm
������������õ��ļ���srcĿ¼�£�tcprstat tcprstat-static

��RHEL�Ͼ�̬���ӿ�ȱʧ���±���ʧ�ܵ�����ܳ������ʼ�¼֮��
*/