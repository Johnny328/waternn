# Fully-linear DenseNet
Implementation of a Fully-linear DenseNet for inspection of water pipe burst.

## some cmd arguments:
*    --arch  choose a kind of architecture to use
*    --out   the file name of predict result
*    --lr    learning rate 
*    --epoch training epochs
*    --kind   the name of the log file recording information during running
*    --lr_decay learning rate decay
*    --data_dir the path of dataset
*    --save_path the path of saving model (need to change code)
*    --num_init_features an argument of arch waterdsnetf_self_define 
*    --growth_rate an argument of arch waterdsnetf_self_define


### example cmd 1 (for default dataset Anytown) :
python train.py main --arch waterdsnetf --lr 0.6 --epoch 120 --kind Anytown_0307_P10C10_B0105_4M --data_dir ~/water/Anytown_0307_P10C10_B0105_4M  --save_path './water/modelparams' --out Anytown_0307_P10C10_B0105_4M

### example cmd 2 (for dataset Anytown with Duration changed) :
python train.py main --arch waterdsnetf_self_define --num_init_features 320 --growth_rate 32 --lr 0.6 --epoch 120 --kind Anytown_0313_P10C10_B1030_Duration5 --data_dir ~/water/Anytown_0313_P10C10_B1030_Duration5   --save_path './water/modelparams' --out Anytown_0313_P10C10_B1030_Duration5 

### example cmd 3 (for dataset Mudu) ：
CUDA_VISIBLE_DEVICES=0 python train.py main --arch waterdsnetf_in4_out58 --lr 0.6 --epoch 120 --kind Mudu_0317_P10C10_B1030_4M --data_dir ~/water/Mudu_0317_P10C10_B1030_4M  --save_path './water/modelparams' --out Mudu_0317_P10C10_B1030_4M 

## Tricks during training

* diminish learning rate with traning epochs increasing
```
You can directly changde the codes to set the periods of diminishing.
```
* choose a best model with lowest loss since the last time when learning rate changed 
```
If you want to train fast and save space, this is not needed. Acturally, it is commented-out, so you should read the code and reuse it if you want to try this trick.
```

## other super-parameters:
* batch_size
```
Default batch_size is 128, you can change it in the train.py
```
* weight_decay
```
Default weight_decay is 0.00005, you can change it in config.py
```

