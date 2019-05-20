# 编译kubeadm

## 下载kubernetes源码

```bash
    git clone https://github.com/kubernetes/kubernetes
```

### 编译kubeadm 

> 证书有效期10年

```go
 if len(fixtureDirectory) > 0 {
                cert, err := ioutil.ReadFile(certFixturePath)
                if err == nil {
                        key, err := ioutil.ReadFile(keyFixturePath)
                        if err == nil {
                                return cert, key, nil
                        }
                        return nil, nil, fmt.Errorf("cert %s can be read, but key %s cannot: %v", certFixturePath, keyFixturePath, err)
                }
                maxAge = 100 * time.Hour * 24 * 365 // 100 years fixtures
        }
```

## 配置http代理

修改docker.service 文件，添加http代理

```bash
export HTTP_PROXY=http://127.0.0.1:9666
export HTTPS_PROXY=https://127.0.0.1:9666
```
