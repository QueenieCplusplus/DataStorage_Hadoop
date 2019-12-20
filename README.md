# DataStorage_Hadoop
Hadoop 分散式資料存儲

# 資料倉儲

資料倉儲是解決大數據存儲的基礎設施，此系統提供資料備份機制，可以將資料存儲分佈在大量伺服器中，在可靠地多備份儲存的同時，亦能將存取權分佈到叢集中每個伺服器上。Hadoop 會自動備份 3 份！

# 發展起源

GFS...BigTable

# Hadoop 核心元件

                   HBase 資料庫
                  
                    HDFS 分散式存儲系統
                  
                  DataNode 節點
                  
# Hadoop 其他元件

                Spark 處理流程的另一平台

                Yarn 資源設定系統
                
                Mahout 資料採擷工具
                
                Hive 資料倉儲工具
# 資料流程處理

...

# 解決現今當前的問題

1. 資料量
2. 資料類型
3. 處理速度
4. 模型變化

# 面臨的瓶頸與風險

1. Node 單點故障時
2. Cluster Infra Failout 影響可用性與可依賴性
3. Cluster 對數據的隱私安全問題

# 採取相應的對策

1. 提升容錯
2. Facebook 的方案
3. TDH 的方案
