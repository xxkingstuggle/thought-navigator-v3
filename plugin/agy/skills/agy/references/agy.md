# AGY

模型与额度来自运行前 models、/usage、/credits。查询失败或字段不可信时阻塞。安全门禁见引擎 scheduling.py。恢复使用准确 conversation ID，禁止按最近会话猜测。失败检查当前 job 的 result.json、stdout.log、stderr.log、provider.log、attempt-* 与 recovery.json。日志必须脱敏，不输出凭据。
