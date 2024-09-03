![image](https://github.com/user-attachments/assets/1b524986-836d-4eca-a200-dc2d907c5b22)

Nếu bạn bị lỗi này, thì hãy vào check thử xem file đó có tồn tại không, và nếu nó tồn tại và không có nội dung thì bạn hãy xóa nó đi.

Sau khi xóa nó đi thì bạn hãy mở powershell với quyền admin và gõ lệnh (Hãy thay dir phù hợp với máy bạn nhé):

```
kubectl config view --raw > C:\Users\LEGION\.kube\config
```

Sau đó check lại:

```
kubectl version --kubeconfig="C:\Users\LEGION\.kube\config"
```

Sau đó chắc chắn bạn vẫn bị lỗi `kubernetes failed to start docker desktop`. Thì giờ bạn hãy vào `bug icon` ở góc phải trên cùng.

![image](https://github.com/user-attachments/assets/fa627c5d-180a-4310-9fb4-1e462241a0f9)

Sau đó bạn delete 3 cái này và restart lại là vào được.

# REFERENCES
[1]. https://kubernetes.io/docs/reference/kubectl/generated/kubectl_config/kubectl_config_view/
