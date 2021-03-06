# DataStorage_Hadoop
Hadoop 分散式資料存儲，引領去 IOE 風潮 (IBM, Oracle, EMC 這些昂貴又難以維護的資料庫系統。)

https://piazza-resources.s3.amazonaws.com/ist3pwd6k8p5t/iu5gqbsh8re6mj/OReilly.Hadoop.The.Definitive.Guide.4th.Edition.2015.pdf

# 資料倉儲

資料倉儲是解決大數據存儲的基礎設施，此系統提供資料備份機制，可以將資料存儲分佈在大量伺服器中，在可靠地多備份儲存的同時，亦能將存取權分佈到叢集中每個伺服器上。Hadoop 會自動備份 3 份！

# 發展起源

GFS...BigTable （TBD）

# Hadoop 核心元件

                      HBase 資料庫
                  
                    HDFS 分散式存儲系統
                  
                     DataNode 節點
                  
# Hadoop 其他元件

                       Spark 處理流程的另一平台

         Yarn 資源設定系統 // Spark 則是運用 Standalone // Apache 使用 Mesos
                
                        Mahout/R 資料採擷工具
                
                           Hive 資料倉儲工具
# 資料流程處理

資料流程指的是一個持續不斷的無序資料集，而資料流程處理是把連續不間斷的資料登錄分割成單中繼資料塊 chunk or block。

面對源源不斷的資料流程流過系統時，系統能夠不停地連續計算，所以系統上沒有嚴格的時間限制，資料從進入系統到結果出爐需要些時間。

# 解決現今當前的問題

1. 資料量
2. 資料類型 (眾多資料來源)
3. 處理速度 (考驗處理上的低延遲)
4. 模型變化

# 面臨的瓶頸與風險

1. Node 單點故障時
2. Cluster Infra Failout 影響可用性與可依賴性
3. Cluster 對數據的隱私安全問題

# 採取相應的對策

1. 提升容錯
2. Facebook 的方案
3. TDH 的方案

# 安全與隱私

(1) 啟動大數據專案前，需要考量安全問題。

(2) 計劃使用存儲和傳送資料時，要遵守安全規範，避免資料遺失，造成名譽受損。

(3) 需要執行存取控制等政策。

(4) 對靜態和動態資料進行檔案層加密，當資料從節點到應用程式之間相互傳遞與移動時，可採行 SSL 加密。

(5) 金鑰管理與被保護的資料需要分開。

(6) 採用 Kerberos 協定作為網路身份識別控制，有效保護叢集中沒有流氓節點。

(7) 節點之間或是節點與應用程式之間採用安全通訊協定 SSL。

# 4A, 角色許可權管理

透過 Kerberos 作為 ID storage, 透過 LDAP 管理 accounts，平台結合 LDAP 做到 Role Base Access Control。

* Authentication 認證

* Authorization 授權

* Audit 稽核

* Account 帳號

# key in Session, 加密的安全通訊技術



                          Key Assigning Center (CA)
                
                        / /
                       / /
                      / /
                            
                 Client       ___ ___ ___     Server


1. Client 將 request 和 decript Cert 發給給 CA ，CA 返回一個 Auth 授權，並且產生 Sesseion Key，作用於 C/S 之間的身份驗證。

2. CA 將 session 的 key + username + user IP + service name + valide time + timestamp 包裝成為 Cert，發給 client，Cert 和 session key 都是經過加密後方才返回給 Client 的。

3. Client 收到 CA 給的這份 Cert，同時間將收到的 session key 解壓縮並且將自己的 username + user IP 包裝封裝後成為 session key，並且 encrypt 此封裝物件，爾後將 Cert 與 session key 發給 Server。

4. Server 收到後，利用 Cert 與 CA 給的 key，將此 Cert decrypt，近一步獲得 user資訊，方才回傳 response。

備註：

Cert, Certificate 又稱為票據或是電子憑證

Token, 權杖

Key, 金鑰

# 安全檢查清單表

1) 管理員的帳密是否經過合理的管理

2) 是否安裝防火牆

3) 防火牆是否經過合理的設定

4) 底層系統是否安裝最新版本

5) 是否安裝網路的防毒軟體

6) 是否有關閉不需要使用的服務通訊埠

7) 是否對系統記錄有做監測

