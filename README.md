Get jenkins Repositaries

```
sudo curl -o /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
```

import jenkins required key
```


sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
```

Add required dependencies for the jenkins package
```


sudo yum install fontconfig java-17-openjdk
```

intall jenkins

```
sudo yum install jenkins
```

Deamom reload

```
sudo systemctl daemon-reload
```

Start jenkins

```
sudo systemctl start jenkins
```

Enable jenkins services

```
sudo systemctl enable jenkins
```
