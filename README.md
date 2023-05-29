# on-8051-iap
为at89c52内存划分两个空间，分别存储boot_loader和app，_easy;
里面boot_loder项目里只做了一个简单的流水灯用以验证代码是否成功运行,之后跳转到app项目的运行入口地址，可以自主在boot_loder里面编写代码以更新app内存储，
注意isp烧录时先清空缓存之后先载入app程序（这里app程序需要在项目里面和设置从0x1000开始生成代码，isp设置从0x1000开始写入），
然后取消清空代码缓存区，再载入boot_loder代码(默认工程即可，从0x000地址开始生成代码iap里面改为0x000开始生成载入代码)这样缓存区0x1000之前的空代码就会被替换为 boot_loder的代码
烧入即可,这样两个工程就分别被载入rom代码缓存区的0x0000-0x0FFF和0x1000-0x2000;
