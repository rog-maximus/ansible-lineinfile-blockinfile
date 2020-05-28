# ansible lineinfile blockinfile module用法

## blockinfile
在LLLL之後插入
123456|!@#$%^T^&*((()))[[[]{}]]
```
  tasks:
   - name: test
     blockinfile:
       path: /tmp/maximus.txt
       marker: ""
       insertafter: "LLLL"
       block: |
         123456|!@#$%^T^&*((()))[[[]{}]]
```

