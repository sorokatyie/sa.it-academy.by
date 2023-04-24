# 12. Kubernetes. Data. Security

## nginxd.yaml

```yaml
---
apiVersion: v1
kind: ConfigMap
metadata:
  name: test-config
data:
  index.html: |
    <!DOCTYPE html><html><body>
    <h3>Nginx container</h3>
    <h1>_HOSTNAME_</h1>
    </body></html>

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 3
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: "33%"
      maxUnavailable: "0%"
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
        resources:
          requests:
            cpu: 50m
            memory: 50Mi
          limits:
            cpu: 100m
            memory: 100Mi
        volumeMounts:
          - mountPath: /usr/share/nginx/html/
            name: index
          - mountPath: /root/.ssh/
            name: ssh-key

      initContainers:
      - name: test
        image: nginx:latest
        command: ["bash", "-c"]
        args:
          - cd /tmp;
            sed -e "s/_HOSTNAME_/$HOSTNAME/" index.html > /usr/share/nginx/html/index.html;

        volumeMounts:
        - name: test-config-mount
          mountPath: /tmp/index.html
          subPath: index.html
          readOnly: false
        - mountPath: /usr/share/nginx/html/
          name: index
        - mountPath: /root/.ssh/
          name: ssh
      volumes:
      - name: test-config-mount
        configMap:
          name: test-config
      - name: index
        emptyDir: {}
      - name: ssh
        emptyDir: {}
      - name: ssh-key
        secret:
          secretName: test-keys

---
apiVersion: v1
kind: Service
metadata:
  name: nginx
  labels:
    run: nginx-service
spec:
        #type: LoadBalancer
  ports:
  - port: 80
    protocol: TCP
  selector:
    app: nginx

---
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: ingress-sa
  annotations:
    kubernetes.io/ingress.class: nginx
    nginx.ingress.kubernetes.io/server-alias: "nginx-test.k8s-14.sa"
spec:
  rules:
    - host: nginx-test.k8s-14.sa
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: nginx
                port:
                  number: 80
```

## secret.yaml

```yaml
---
apiVersion: v1
kind: Secret
metadata:
     name: test-keys
type: Opaque
data:
    id_rsa: (private rsa key in base64)
    id_rsa.pub: (public rsa key in base64)
```

## sealer_secret.yaml

```yaml
---
apiVersion: bitnami.com/v1alpha1
kind: SealedSecret
metadata:
  creationTimestamp: null
  name: test-keys
  namespace: default
spec:
  encryptedData:
    id_rsa: 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
    id_rsa.pub: AgDBIxXY8tAv+2YA55BRVmG5llIBj2obEKE6pjilwuayyEcP+ZF9KhkTPIbi6sHg8SErxQ5929vtfIb2sWhhUtH4rOkmm+GYKNOuf33UxVfGajxCBA8sHNeCRo6L1sUwphS23UMAKBrrkivDf7qgKA/b5Oxpw7Jc/o+AlLvoSNYwJ/9r9GBgWLlv+nCbng9anpB/nm+nUkYN2bWoj4kKNv325HhVQZoOqmGT1mkrbfwU7HK+FKWygIsP4kDQH+MoGD/QsxX7ndzNqzCwc6VfAEIQaBo4TOdM5yBeBwqAU2uYK+UrXbMlThxCylXTXBbBNFRIjhXAqC3jRWWWNe/woThBbBst1/z2MlzEgeCizeVH05uxUcRTFtKNNiY9qKRFNCMfEfxC77op8I+RIjc7pbqmjjCMf0p3lPIzOc4fe0eDsE8p9zH88PXB+LyJXcD+36NsDtk6Bq4NpqevVmFkgmPYjMDTGbDqX0BgbiKpnDbLfDHmBGvwJyJNHjH1QRKtcvGFgGWPuqkyg4jz4ToEgLvJediJqcdDyV6fSHFud8bbiN3eb/75OuN6EsKjI4gVWbE7E34OvCHlrCG+sG5A8Rype0aAyakWKSawn6dUGeKws5oalatB+BHOL1Ij8NUcnkeo4lMkGeutukQSThUsR8DFW/2WVT42eTJLIoGu5V62IEPUTi9xvOE0FQYZOerdXXnPrmmwkoLVo4yz53UTSvrDs6DKx0j+Ia5ItaIMOe7McM++5p/qK/pHC9h1Kb+dyiEaXeRpJ/J1z2b+3wapoiRYz270Rq9DwTSKwF7a0vhRXcTvnn9Vg64t4xHJk6v9azUDfBTc7STT9hzMzKvWncArdR3gP/QcBExdFANpW02wRhSgwwWA0SARPCDn+HnW4Tn0jjA9+RHEmS9lwuYjRvq1msWB02SscPzhnr8QecsaVjYUjtfFldh1LROx5rJQdaQmEjeNTk4YvvBfupkpHF1NLv3kIhENXiKgiqiG3po52wb0PA9ON35KrNCfCPZPxLRDFVlY47Uop6y81U6Ohvto/DxS8JMYlnShD864tqjuibSnV+NcNAnR3tOsRQ2y1rHwaHR5nnf7j2EeOOBu4QNXgepF9Xnjnt0Nn3GOIEZDbMNNc2nH+PNVN1n6v73AbCnH5l8PejgqoGxwqBy3XnaSm7ZYN9d3HTM1yuJwjxSTohC2dAhF1Ctoig+NMWT4QM/tYKsL5Mm0zKnQBTjmjPeEYonO33D6N0M/jqvjj4l3iJEFIoRUjTneSaRMLfUHlpvlSrT27z+V0ckIzd3RmNFrwJQZ8+ck89PIPFrq1pA8MUQ9il8jIv+NheSWUeonRtOSTXP5Z5eVA4cp6yNExflHer+QdNFANwozV59BSwNlig91RN2Xl4GS7BPcYGEH3yZ2t78mLB4plTSRH+3plCT0+5XvISO4WgNfnnw4/lee7MbC3g==
  template:
    metadata:
      creationTimestamp: null
      name: test-keys
      namespace: default
    type: Opaque

```

## Pods

![index](https://github.com/Anton50013/sa.it-academy.by/blob/md-sa2-23-23/Anton_Negovora/12.Kubernetes.Data.Security/index.png)

## Sealed secret

![describe](https://github.com/Anton50013/sa.it-academy.by/blob/md-sa2-23-23/Anton_Negovora/12.Kubernetes.Data.Security/describe.png)

## SSH Pod

![pod](https://github.com/Anton50013/sa.it-academy.by/blob/md-sa2-23-23/Anton_Negovora/12.Kubernetes.Data.Security/pod.png)
