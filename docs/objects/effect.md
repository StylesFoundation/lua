# PotionEffect

药水效果

### 方法

|  方法名   | 类型  | 参数  | 说明 |
|  ----  | ----  | ----  | ---- |
|  get_duration   | int  | void | 药水的剩余时间，单位为tick，除以20可以算出秒数 |
|  get_name   | string  | void | 药水的命名空间名，例如`potion.moveSpeed` |
|  get_id   | int  | void | 药水id |
|  get_level   | int  | void | 药水等级，请注意如果药水为II级别会返回1，如果是1级会返回0，从0开始，以此类推 |