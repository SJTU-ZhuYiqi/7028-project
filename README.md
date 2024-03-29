# zi2zi: Master Chinese Calligraphy with Conditional Adversarial Networks

## Sh命令

#切换目录
1.cd C:\Users\sjtuz\Desktop\7028\team project\project-7028

#绘制训练集数据

2.python font2img.py --src_font="C:\Users\sjtuz\Desktop\7028\team project\project-7028\dataset\simkai.ttf " --dst_font="C:\Users\sjtuz\Desktop\7028\team project\project-7028\dataset\STXINGKA.ttf " --charset=CN --sample_count=200 --sample_dir=dir --label=0 --filter=1 --shuffle=1

#训练集与验证集分离

3.python package.py --dir=dir --save_dir=binary_save_directory --split_ratio=0.8

#移动训练集、验证集

4. move .\binary_save_directory\*.obj .\experiment_dir\data\


#训练神经网络（下面两句选一句即可）

5.python train.py --experiment_dir=experiment_dir --gpu_ids=cuda:0 --input_nc=1 --batch_size=128 --epoch=10 --sample_steps=500 --checkpoint_steps=10

python train.py --experiment_dir=experiment_dir --gpu_ids=cuda:0  --batch_size=32 --epoch=50 --sample_steps=200  --checkpoint_steps=5000

#让神经网络进行字体转化（以从楷体出发为例）

6.python infer.py --experiment_dir experiment_dir --gpu_ids cuda:0 --batch_size 128 --resume 20 --from_txt --src_font ./dataset/simkai.ttf --src_txt 朱奕奇最帅

