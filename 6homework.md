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


