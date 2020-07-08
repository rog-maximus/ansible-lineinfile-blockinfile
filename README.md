# ansible lineinfile blockinfile module用法

## blockinfile
在LLLL之後插入
123456|!@#$%^T^&*((()))[[[]{}]]<br />
marker: "" 這邊可以填寫你要標注的項目(這邊不添加會顯示兩行原本擁有的)
```
# BEGIN ANSIBLE MANAGED BLOCK
123456|!@#$%^T^&*((()))[[[]{}]]
# END ANSIBLE MANAGED BLOCK
```
```
  tasks:
   - name: test
     blockinfile:
       path: /tmp/maximus.txt
       marker: "#你想要標注的項目在開始這邊"
       insertafter: "LLLL"
       block: |
         123456|!@#$%^T^&*((()))[[[]{}]]
```

## lineinfile

以下為開頭是LLLL的取代為line裡面的內容

```
   - name: test
     lineinfile:
       dest: /tmp/maximus.txt
       regexp: '^LLLL' 
       line: |
         1 
         23
         {}{{}{!@#%^&^%*(^&*()*&)}}
```

在L開頭前面插入11111111111111

```
   - name: httpd.conf modify 8080
     lineinfile:
       dest: /tmp/maximus.txt
       insertbefore: '^L'
       line: |
         11111111111111
```

在L開頭之後插入11111111111111

```
  tasks:
   - name: httpd.conf modify 8080
     lineinfile:
       dest: /tmp/maximus.txt
       insertafter: '^L'
       line: |
         11111111111111
```
刪除1111開頭的那一行

```
   - name: httpd.conf modify 8080
     lineinfile:
       dest: /tmp/maximus.txt
       regexp: '^1111'
       state: absent
```

官方網站介紹的這一種用法，是拿來定位用的，在#Listen開頭之後的開頭Listen，取代成Listen 8080

```
- name: Ensure the default Apache port is 8080
  lineinfile:
    path: /etc/httpd/conf/httpd.conf
    regexp: '^Listen '
    insertafter: '^#Listen '
    line: Listen 8080
```

官網:
https://docs.ansible.com/ansible/latest/modules/lineinfile_module.html


參考:
https://blog.51cto.com/zouqingyun/1882367
