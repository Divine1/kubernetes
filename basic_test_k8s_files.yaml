pcgames_pod.yaml 
```
apiVersion: v1
kind: Pod
metadata:
  name: pcgames
  namespace: pcgames
  labels:
    app: pcgames
spec:
  containers:
  - image: public.ecr.aws/o9q7s3h0/pcgamesapp:latest
    name: pcgamesappcontainer
    ports:
    - containerPort: 4000
```

pcgames_clusterip_service.yaml 
```
apiVersion: v1
kind: Service
metadata:
  name: pcgames
  namespace: pcgames
spec:
  selector:
    app: pcgames
  ports:
    - protocol: TCP
      port: 8180
      targetPort: 4000
```

pcgames_ingress_http.yaml
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: pcgames
  namespace: pcgames
  labels:
    app: pcgames
spec:
  ingressClassName: nginx
  defaultBackend:
    service:
      name: pcgames
      port:
        number: 8180
  rules:
    - host: pcgames.mangotree.click
      http:
        paths:
          - pathType: Prefix
            backend:
              service:
                name: pcgames
                port:
                  number: 8180
            path: /
```

pcgames_ingress_https.yaml 
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: pcgames
  namespace: pcgames
  labels:
    app: pcgames
spec:
  ingressClassName: nginx
  defaultBackend:
    service:
      name: pcgames
      port:
        number: 8180
  rules:
    - host: pcgames.mangotree.click
      http:
        paths:
          - pathType: Prefix
            backend:
              service:
                name: pcgames
                port:
                  number: 8180
            path: /
  tls:
    - hosts:
      - pcgames.mangotree.click
      secretName: pcgames-tls
```

pcgames-tls_secret.yaml
```
apiVersion: v1
kind: Secret
metadata:
  name: pcgames-tls
  namespace: pcgames
data:
  tls.crt: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUM1RENDQWN3Q0NRRGMwZE9PSHlXTjhEQU5CZ2txaGtpRzl3MEJBUXNGQURBME1SNHdIQVlEVlFRRERCVncKWTJkaGJXVnpMbTFoYm1kdmRISmxaUzVqYjIweEVqQVFCZ05WQkFvTUNXMWhibWR2ZEhKbFpUQWVGdzB5TWpBMQpNVFl4TURVeE5EZGFGdzB5TXpBMU1UWXhNRFV4TkRkYU1EUXhIakFjQmdOVkJBTU1GWEJqWjJGdFpYTXViV0Z1CloyOTBjbVZsTG1OdmJURVNNQkFHQTFVRUNnd0piV0Z1WjI5MGNtVmxNSUlCSWpBTkJna3Foa2lHOXcwQkFRRUYKQUFPQ0FROEFNSUlCQ2dLQ0FRRUEzSHFLekNZcjE1dEliTTcyMnRpLzVubHplVkU4RVlzeTBlS0dIYWRvRy9tYQpZRWJ1dGlJRkZicUdPeWErNXVPNVBHOVdOSy93UjEvOUFNY0YxUDI4L3RZNGVBMlplTFNlczJaYVlCK25INlhWCnNjVDd1dzBJc053WHpjdGI5VGZpOHRXWDhqTGZHZ2JhTkJOekUvWUk0dEVNTVRLMVFqSEZMOVZoRGhVajRRdngKSzRHTWxZZUVtek4vQ1FFK25OcFd0OUJxMVFoMlR0WnRMRWJvS1Q0K0gvSVJ0TmswcjBnZzUvcllYbnhRN2JpRQpSOHJGR1B3R2M2S1BScDBXV0ZDaE1SNFBYTXprWFNvLzZpbVRYRUQ2OXA3aGY2TXVSUW5id0RoVmkrd0ZxRW02CjkwUi9IazRwYXRxZ3pZZDAzM1pjdmVONFhsdTN3K3lIeEZaYTZBajNRd0lEQVFBQk1BMEdDU3FHU0liM0RRRUIKQ3dVQUE0SUJBUUNhaUhUaXVZdFpqbmpWdXdXQjBsdVJOek95dUtQSkE5RXloNXZUQVZsOUlKL1FvQ0l2NzFtdwpXR0cwRXdYbi9EbHlYUU44TW5lTmp0VUQra1lDWm05bWJlRFpiUzBraTBoUWRKMDgraXFZZW0rOXdpU1BxYmtYCm9OcTRZZVhsOC8vaFpnNGdOK0o0QW85ejhqc01rbVNtbHkxcXlIMnFTSEtCNW42QVVqMHgwbVdZNFJpbXVWSlAKcDE5d29nUjdGUDBJNllLa082NG00SkJvVGd6MWYzSFR3bExjclRkUDJhd3JFby9pVTdSZ0N5TXFMYXlNaEpjZwo2aFRIKzc3L0RYV1RLZENDbTErUStaaWEvMlZ3UWQrKzdnb2F2WVZLSUdTbGhENTJPZDhidXR2bSttTk9TYm1KCklZTHVIeWNQRWcvSElpdG12MVdqTFl6Rzl6SXZXdkVuCi0tLS0tRU5EIENFUlRJRklDQVRFLS0tLS0K
  tls.key: LS0tLS1CRUdJTiBQUklWQVRFIEtFWS0tLS0tCk1JSUV2UUlCQURBTkJna3Foa2lHOXcwQkFRRUZBQVNDQktjd2dnU2pBZ0VBQW9JQkFRRGNlb3JNSml2WG0waHMKenZiYTJML21lWE41VVR3Uml6TFI0b1lkcDJnYitacGdSdTYySWdVVnVvWTdKcjdtNDdrOGIxWTByL0JIWC8wQQp4d1hVL2J6KzFqaDREWmw0dEo2elpscGdINmNmcGRXeHhQdTdEUWl3M0JmTnkxdjFOK0x5MVpmeU10OGFCdG8wCkUzTVQ5Z2ppMFF3eE1yVkNNY1V2MVdFT0ZTUGhDL0VyZ1l5Vmg0U2JNMzhKQVQ2YzJsYTMwR3JWQ0haTzFtMHMKUnVncFBqNGY4aEcwMlRTdlNDRG4rdGhlZkZEdHVJUkh5c1VZL0Faem9vOUduUlpZVUtFeEhnOWN6T1JkS2ovcQpLWk5jUVByMm51Ri9veTVGQ2R2QU9GV0w3QVdvU2JyM1JIOGVUaWxxMnFETmgzVGZkbHk5NDNoZVc3ZkQ3SWZFClZscm9DUGREQWdNQkFBRUNnZ0VBRDZNQlJRbFFBcktZcUY3bFV4QWNUQlJCQkZHbW1QZnVXc1JlRHF4WXplTWQKOThZUUdBckJvWkRoQkVEek9SemRmbFBISVdWNC9SYnBzcXhxMVhoSmR5bHFSOWx2RVFoK1dPcmhiZi9Rc29YbwphZnMyZjBXbFlDVzc2blNKeVJKMW5oTlgrMjF3TlVCWEtXcFh0d3EwQnFJYzQwQmRhcHh0Qjc5eWFyVkZIaWpBCjZpb3hRUmtzc0ZLQ095aWZ1aVo0QUZjZ2dYYi8wMXNxNXEzUTZTSzNuejAyenBoU1BKdkIyWDRIRFlYdkJRNW8KY05wV0RoNnRteGFPZ1ZiV04ycWlpVWlONFdCZVV0VWp2anJzVmZQYWVqV21xL2lSV3NYVmdTdFFScEZPaXNhRgpFU3NLOXQ2ZGJianpBcE1uSjFpeDZoYm83TkNSZEpJM0gwb2lhUGNpUVFLQmdRRDY1RTUyeHgvalA5UnN1dlR5CnJlQmZzQXZEY2ZnSlJCYVZ3TmlDUnVBOXJUSDUrVFg3bitmbElxdHpVbUU5N3ZyeDdMRmtqZkpmcTNmSkh1clIKSXJkbWRWbDRzbWpENUc4SGNGUk9UQmZmbm9hN3N2dERTM0JNdHdUVkVISnJ0NDV1ZXRvMU11bndFMzgrQ0dyZgpFYTRSZk5KM2VkeFFPeTZzb056anRhTklqUUtCZ1FEZzk3ZUYrNmVrVzlzdmc2VjVLaDVxK3BqOFpOcVphakx3CmJ1cXM0Ym9NcllicmRoRlUvUHI1MUV4SHhWVDhXOXBaam4rcE9HR1IrYnBVQ2xJOVg5bmttTW5zQ2hvZWlHY2sKQlpVOUZYQUYzRVhzYmZidm8waDRMYnBBZlNaN3dOMnMvN2E2bk4vTkpvbWNUQXJkZkxkN0lOc1U5TGZtSmtnQgoxSWpMTHpwVER3S0JnUURLSDdCTzVMRDk1V2gvaUViYVU5WlZnSUNabm5HVEZYV1VnOTVwWml3MXhCaGxLSzZpCjN2cDFrTzdMWTJ6UDluM1k5VFVjcTNhK09HZXljZVAvUkphNFJvWWtSS2MrV2dSUTIrQXZqQUlYdDZFWUNtTisKbllJRmE5VEt5Z3RFV0lhNDN1UjR3MkhRZGdTbXR5VlNQTzRkVEpCS2pMUS9OczZ0YUpOTUtBTTU2UUtCZ0dCdwo4WVVIbUJ0Mm9XVWlHNHJ3eW05MEZLZUdtTXZSNGhwK2dpNHc2bkJLNTU4RFUzVEtxdEQwK09wL3B1bzBla3VRCk1od2FKb0hNdTlzUlBhWS85QW55a2dXVll4TVp5SldCcXpPdmdBR1RKNHF1cllDWDBCWnRDLzVmYUdML0VFajgKcXBvZmJEWG5RbkQxakdiYzgwOWVpMnpWYUF6SzltMktia1lrYmUxekFvR0FabXVCaDRvL09GOFNtN1FadngycQowQUg5SzZQaTRta0tra0owNkpSb01yNllOZVo2WnVwd29YMGdPY1Roc1R1MGZYTmVEbEhOMTZnVjFod0t3S3RGCnNsTGtjUzQrK1hjaE5VUktoU2pJSWxHNng1d3ZPSG5oUWhJaUpJUDVucU0zTUhoMjJvL1FhV3R1eXp0NDA5b2oKa2pIZVo1aHlrajNQcDk1RGlJd3hEcXM9Ci0tLS0tRU5EIFBSSVZBVEUgS0VZLS0tLS0K
type: kubernetes.io/tls
```
