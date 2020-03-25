---
title: �¹�����δ��Уδ������N��֮���Զ��򿨡�
date: 2020-03-25 08:22:42
tags: 
- Python
- �ű�
- POST
categories:
- Backend
- Python
---


{% note info %}
����»��ô�һֻ����˵��...  
���ˣ���������3��룬�һ�������Ͽ��Timing,ͻȻ��X�͸���˸��绰����˵�����Զ��򿨵��뷨...  
����������������������Ҫÿ�콡���򿨻㱨��ѧУ��Ȼ��ÿ���ύһ����̫�鷳�ˣ�����д�������Զ���...
�Һ���X�͸�ȷ��˼·�������·�� 
1. ����javaд����̨�Զ�ˢ���˵ģ���Ū����ҳ���û���д�˺����뱣�������ݿ⣻
2. ����ľͺ�ֱ�ӣ�ֻˢһ���˵ģ�pythonģ���������¼���,�����ö�ʱ���񣨶������趨�������
{% endnote %}

<!--more-->
# Windows����Ч��
{% asset_img result1.png �򿨳ɹ� %}
{% asset_img result.png �ظ��� %}

# ���Ĵ���
> ���ú��Ϲ���ѧԺ�Ĵ�ϵͳ��  
�������ô����ύ��ʵ������Ϣ���������齫�ܵ���ط��ɴ���

```py ģ���¼�� https://github.com/Lruihao/python-funny-code/blob/master/%E6%98%93%E7%8F%AD%E6%89%93%E5%8D%A1.py ��������
def lajaDaka():
  # ��¼
  r1 = requests.post(login_url, data=login,headers=headers,verify=False)
  if r1.status_code == 200:
    print(time.strftime("%Y:%m:%d:%H:%M", time.localtime()))
    print(login["username"],"��¼�ɹ���")
    # �õ���¼���cookie����ӵ�header��
    header1 = r1.headers
    headers["Cookie"] = header1["Set-Cookie"]
  else:
    return

  # ��
  r2 = requests.post(daka_url, data=daka,headers=headers,verify=False)
  response2=r2.json()
  if r2.status_code != 200:
    print("��ʧ�ܣ�")
    return
  if response2["result"] == True:
    print("�򿨳ɹ���")
  else:
    print(response2["errorInfoList"][0]["message"])

if __name__=="__main__":
  lajaDaka()
```

# �Զ�����
## Windows
����python�����������ʱ��
```py ��ʱ
if __name__=="__main__":
  while True:
    now_hour = time.strftime("%H", time.localtime())
    now_min = time.strftime("%M", time.localtime())
    # ����ÿ��8�㷢��
    if now_hour < "08":
      rest = 8 - int(now_hour)
      sleeptime = (rest-1)*3600 + (60-int(now_min))*60
      print("����ʱ����ʱ��Ϊ��"+time.strftime("%H:%M", time.localtime()),"\t�ű�����",rest-1,"Сʱ",int((sleeptime-(rest-1)*3600)/60),"���Ӻ��")
      time.sleep(sleeptime)
    elif now_hour > "08":
      rest = 8 - int(now_hour) + 24
      sleeptime = (rest-1)*3600 + (60-int(now_min))*60
      print("����ʱ����ʱ��Ϊ��"+time.strftime("%H:%M", time.localtime()),"\t�ű�����",rest-1,"Сʱ",int((sleeptime-(rest-1)*3600)/60),"���Ӻ��")
      time.sleep(sleeptime)
    elif now_hour == "08":
      print("������쿪ʼ����ÿ��8�㷢�����ݣ�")
      lajaDaka()
      time.sleep(24*60*60-int(now_min)*60)
```

## linux(�Ʒ�����)
�python��������������ʹ��shell�ű���ʱִ�С�
```bash �ű������趨
python /home/python/yiban_daka/daka.py
```
[CRON���ʽ�Ļ����﷨](/posts/cron.html)

# ��x�͸��java web�汾
���ϳ���Ա��Ӧ���еļ��ͷ��㣬�ɾ���������
`http://39.105.174.214/index.html`
{% asset_img javaweb.png java web�� %}
