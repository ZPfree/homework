基础作业
数据集显示

![image](https://github.com/ZPfree/homework/assets/16116418/ac706ca2-5b7a-4e46-8a9a-01ec54e3654f)

正常显示各个数据的结果

![image](https://github.com/ZPfree/homework/assets/16116418/e3644316-ed89-4419-8c5a-be12a39c1b28)


![image](https://github.com/ZPfree/homework/assets/16116418/42dc882b-8d56-47d1-9e1c-4771bc45af51)


进阶作业





安装了opencompass0.2.0 并参考前面提交作业的环境解决。
这个模型是直接lmdeploy lite auto_awq  /share/model_repos/internlm2-chat-7b/ --w-bits 4 --w-group-size 128 --work-dir ./internlm2-chat-7b-4bit --calib-dataset "c4"
python run.py --datasets ceval_gen --hf-path  /root/internlm2-chat-7b-4bit/ --tokenizer-path /root/internlm2-chat-7b-4bit/ --tokenizer-kwargs padding_side='left' truncation='left' trust_remote_code=True --model-kwargs trust_remote_code=True device_map='auto' --max-seq-len 2048 --max-out-len 16 --batch-size 1 --num-gpus 1 --debug

效果居然这么差？？ 待重搞

![image](https://github.com/ZPfree/homework/assets/16116418/b508873b-28b8-4cdd-9930-1868b159aba5)
![image](https://github.com/ZPfree/homework/assets/16116418/3865a2af-5111-483e-ae5a-e2358858df51)

![image](https://github.com/ZPfree/homework/assets/16116418/d57389b2-3640-40e3-bd97-695c52c5e85a)

进阶作业重做参考https://kvudif1helh.feishu.cn/docx/U22sd7lfbo5YFPxgm5Vcm4s1nzh

W4 量化
lmdeploy lite auto_awq  /root/ft-medqa/merged/ --w-bits 4 --w-group-size 128 --work-dir  ./internlm2-chat-7b-4bit

转换成turbomind
lmdmdeploy convert internlm-chat-7b ./internlm2-chat-7b-4bit --model-format awq --group-size 128 --dst-path ./workspace_w4quant
这个转换指令文档没有注意 convert 后是值要转的类型导致UnboundLocalError: local variable 'head_num' referenced before assignment
启动
lmdeploy chat turbomind ./workspace_w4quant
![image](https://github.com/ZPfree/homework/assets/16116418/69ed62e0-221d-4b1f-8c59-35d976a80c74)
![image](https://github.com/ZPfree/homework/assets/16116418/74631903-3c27-4754-bd15-402b8b66a3a2)

python run.py configs/1.py -w outputs/w4result
结果如下

![image](https://github.com/ZPfree/homework/assets/16116418/bfec315c-73d5-44f5-99f8-9653d4039e87)
![image](https://github.com/ZPfree/homework/assets/16116418/a31216c4-c78d-4dab-a915-d10c76170a6d)
![image](https://github.com/ZPfree/homework/assets/16116418/16c44eb5-d91f-4697-b8d9-74962a343c76)


opencompass 评测的是turbmind 模型 不是直接的，第一步差的原因可能是少了这步。
