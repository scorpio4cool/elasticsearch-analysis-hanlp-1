# elasticsearch-analysis-hanlp

安装步骤： 

1、下载插件并解压到es的plugins目录下

	修改analysis-hanlp目录下的hanlp.properties文件，修改root的属性，值为analysis－hanlp下的data 目录的地址
	
	修改analysis-hanlp目录下的plugin-descriptor.properties文件，
	修改elasticsearch的版本为你当前的版本elasticsearch.version=你的es版本号(like:5.5.1)

2、修改es config目录下的jvm.options文件，最后一行添加

	-Djava.security.policy=/home/es/elasticsearch-7.0.1/plugins/analysis-hanlp/plugin-security.policy(地址换成你自己的地址)

重启es

	GET /_analyze?analyzer=hanlp-index&pretty=true 

	{ 

	"text":"张柏芝士蛋糕店" 

	}


测试是否安装成功


analyzer有hanlp_max_word（索引模式）和hanlp_smart（智能模式）

hanlp_max_word：尽可能的切分多的结果

hanlp_smart：切分少的词

自定义词典：

	修改plugins/analysis-hanlp/data/dictionary/custom下的 我的词典.txt文件

	格式遵从[单词] [词性A] [A的频次]

	修改完后删除同目录下的CustomDictionary.txt.bin文件

重启es服务

首次启动hanlp会生成相应的文件，首次启动可能会慢一点
