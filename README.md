# ansible lineinfile blockinfile module用法

## blockinfile
在LLLL之後插入
123456|!@#$%^T^&*((()))[[[]{}]]<br />
marker: "" 這邊可以填寫你要標注的項目
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

