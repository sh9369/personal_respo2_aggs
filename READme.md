# personal_respo2_aggs
this code is for aggs_index
# ǰ��<br>
���������ڻ�ȡ�����鱨�����imap�м�¼��Ŀ��ip��ַ���м�飬��Ŀ��ip���鱨�г��ֵ�ipƥ�䣬�򷢳��澯��Ϣ�������澯��Ϣд��ES�С�<br>

����������Linux���������У�����python 2.7�﷨�淶��д����Ҫ��������������£�
json��logging��datetime��time��elasticsearch��ConfigParser��socket��struct��re��requests��bs4��lxml
<br>
������GitHub��ַΪ��https://github.com/sh9369/personal_respo2
<br>
## ����
1. GitHub��ҳ��ʹ��zip������ص�personal_respo2-master.zip����ѹ���personal_respo2�ļ��У���ʹ��git clone ����ֱ�����ء���Ҫ���ļ�Ŀ¼��ʽ���£�
```
personal_respo2:
|����project��				�������ļ�Ŀ¼
    |����data: 				�������ݴ��Ŀ¼
        |����log��			��־�ļ�Ŀ¼
	|����self_blacklist��		���غ������ļ�Ŀ¼
	|����self_defaultlist��		����Ĭ���鱨ԴĿ¼
	|����self_whitelist��		���ذ������ļ�Ŀ¼
    |����get_blacklist��			�����鱨Դ�����ļ����Ŀ¼
	|����MiningServerIPList.py��	���崦�������鱨���ļ�
	|����  ......
    |����lpm: 				lpm�㷨����Ŀ¼
    |����blacklist_match.conf��		���������ļ�
    |����blacklist_tools.py��		���򹫹����������ļ�
    |����update_blacklist.py��		���º������ļ�
    |����match_insert.py��		ƥ���Լ�����ES�����ļ�
    |����ontime_run.py��			�����г���
    |����parser_config.py��		�����ļ����������ļ�
    |����subnet_range.py��		IP�����δ������ļ�
    |����treat_ip.py��			IP�����������ļ�
    |����ip_check_C2.py��			���μ�鴦���ļ�
    |����check_XForce.py��		��ȡxforce��Ϣ�ļ�
```
## ����
2.����ǰ����blacklist_match.conf�ļ��������ò������޸ģ�
<br>2.1 �޸�[frequency]�µ�starttime����ʾ��ʼ���ʱ�䣻
<br>2.2 �޸�[ES_info]�¶�Ӧ��server/dport��Ϣ��
<br>2.3 ��������غ�����������[self_blacklist_path]����blacklist_flg=1��path��Ӧ�ڱ��غ�������Ĭ��Ŀ¼��
��������Ĭ���鱨Դ���������������һ�¡�
<br>2.4 ����������£�������[update_flg]��updateFlg=0���Ա�رո��¹��ܡ�
<br>
<br>3.��װ��ɶ�Ӧpython�汾�Լ��������󣬽���/projectĿ¼��ʹ���������������
<br>nohup python ontime_run.py & 
<br>���ٴλس���
<br>ʹ����������鿴��־�ļ���
<br>tail -50f ./data/log/testlog
<br>��־�ļ����¼���������е������Ϣ����������־�ļ�����д�����ݺ��ʾ�����Ѿ����С�
<br>
<br>
## �����鱨Դ
4.���������鱨Դ�ķ���
<br>4.1 ��/get_blacklistĿ¼���½�һ�������ļ�������ΪXXX.py��
<br>
4.2 ��XXX.py�б�д�������鱨����/��ϴ/�洢���̣���ر�֤���մ洢�����ݸ�ʽ���£�

`{

    "ip1":

        {    #������������ο����������ļ�

           ��subtype������mining_pool��

            ��desc_subtype������... ... "

             ... .... 

        }��

    "ip2":

        {

            ... ...

        }��

        ... ... 

}`
<br>4.3 ȷ�������鱨����Դ�ĸ���Ƶ�ʣ���blacklist_match.conf�ļ���[parse_blacklist]�µ�fun1ĩβ��ӡ�,XXX:frequency"
<br>
<br>
## XForce��Ϣ
5.��ȡXForce ��Ϣ��
<br>5.1 ��Ҫ�ļ��� check_XForce.py
<br>
5.2 ���÷�����<br>
```
import check_XForce as xf
xf.start(1,lists)
```
 #start(stype,values,checkflg=1)Ϊ�������;<br>
 #params: <br>
   stypeȡֵΪ1��2��1��ʾ���Ķ���values��IP�б�2��ʾvalues��url�б�<br>
   values��ʾ�����IP��url���б�<br>
   checkflgĬ��ֵΪ1����ʾд���ļ�����ֵΪ0�����ʾ��д���ļ���<br>
 #return:<br>
   final_dic ���ֵ���ʽ���أ���ѯ������Ϊkey����������ֵΪvalue<br>
 #example for return��
```
{
	"198.54.117.200": {
		"company": "NAMECHEAP-NET - Namecheap, Inc., US", 
        	"cats": {
            		"Botnet Command and Control Server": 43, 
            		"Malware": 43, 
            		"Anonymisation Services": 43
        	}, 
        	"geo": "United States", 
        	"score": 4.3, 
        	"asns": "22612"
    	}, 
    	"197.210.23.55": {
        	"cats": {
            		"Dynamic IPs": 71
        	}, 
        	"company": "VCG-AS, NG", 
        	"score": 1, 
        	"geo": "Nigeria", 
        	"asns": "29465"
    	}
}
```
<br>5.3 ��������Լ�ע����������ļ�check_XForce.py
<br>