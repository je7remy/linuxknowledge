---
tipo: teoria
tags: [moc, cloud, aws, azure, gcp, security, devsecops]
actualizado: 2026-05-30
---

# MOC — Cloud Security

🏠 [[🔒🐧Hub|Hub Principal]]

**Mapa de contenido (MOC)** sobre **seguridad en cloud** (AWS, Azure,
GCP). La nube es donde vive la mayoría de infraestructura moderna —
modelo de amenazas y herramientas son distintos al pentesting tradicional.

## Modelo de responsabilidad compartida

El concepto fundamental:

| | Cliente | Cloud Provider |
|---|---|---|
| **IaaS** (EC2, VMs) | OS, apps, data, IAM, network | Hipervisor, hardware, datacenter |
| **PaaS** (App Engine, ECS Fargate) | Apps, data, IAM | OS, runtime, hardware |
| **SaaS** (Office 365, Gmail) | Data, IAM, users | Todo lo demás |

**Punto clave**: el provider no es responsable de tu **IAM mal configurado**
ni tus **buckets públicos**. Esa es la fuente del **95% de breaches en
cloud**.

## Los 3 cloud providers principales

| Concepto | AWS | Azure | GCP |
|---|---|---|---|
| Cuentas | Account | Subscription | Project |
| VMs | EC2 | Virtual Machine | Compute Engine |
| Storage objects | S3 | Blob Storage | Cloud Storage |
| Networking aislado | VPC | VNet | VPC |
| Firewall instance | Security Groups | NSG | Firewall Rules |
| IAM users/roles | IAM | Entra ID (Azure AD) | IAM |
| Logs nativos | CloudTrail | Activity Log | Cloud Audit Logs |
| Secrets manager | Secrets Manager | Key Vault | Secret Manager |
| Container service | ECS/EKS | AKS | GKE |
| Serverless | Lambda | Functions | Cloud Functions |

## Top vulnerabilidades cloud

### 1. Buckets públicos (S3, Blob, GCS)

El error más común. Buckets con `public-read` permiten download
anónimo de data sensible.

```bash
# AWS: detectar buckets propios públicos
aws s3api list-buckets --query 'Buckets[].Name' --output text | \
  xargs -I {} aws s3api get-bucket-acl --bucket {}

# Buscar buckets de terceros (recon)
# Herramientas: AWSBucketDump, S3Scanner, GrayhatWarfare
```

**Recurrente en breaches**: Capital One (2019), Accenture, Verizon, FedEx.

### 2. IAM permissive

- `*:*` en una policy → permisos completos.
- IAM roles con `AssumeRole` mal configurado.
- Service accounts con permisos amplios.

**Privilege escalation paths en AWS**: ver herramienta **`PMapper`**.

### 3. Credenciales expuestas

- AWS access keys en GitHub commits (`AKIA...`).
- `.env` con secrets en buckets públicos.
- Secrets en code, no en Secrets Manager.

Herramientas de detección:
- **GitGuardian**, **TruffleHog**, **gitleaks**: scanner de secrets en git.
- **GitHub secret scanning**: nativo (gratis).

### 4. Metadata Service abuse (SSRF en cloud)

```
http://169.254.169.254/latest/meta-data/iam/security-credentials/
```

Si una webapp tiene SSRF y corre en EC2, atacante obtiene credenciales
del rol IAM de la instancia.

**Mitigación**: IMDSv2 (requiere tokens), pero MUCHAS instancias siguen
en IMDSv1.

### 5. Networking misconfig

- Security Groups con `0.0.0.0/0` en puertos no-web (SSH, RDP, MySQL).
- VPC peering mal configurado.
- VPN gateway sin MFA.

### 6. Logging/Monitoring desactivado

- CloudTrail desactivado en algunas regiones.
- Logs de S3 desactivados.
- No alertas en eventos sensibles.

## Herramientas cloud pentest

### Multi-cloud

- **ScoutSuite** (NCC Group): auditoría multi-cloud (AWS, Azure, GCP, etc.).
- **Prowler**: AWS focused, ahora multi-cloud.
- **Cloudsplaining**: AWS IAM analysis.
- **PMapper**: AWS IAM privilege escalation paths.

### AWS específicas

- **Pacu**: framework de pentesting AWS (estilo Metasploit).
- **enumerate-iam**: enumera permisos de un set de credentials.
- **CloudGoat**: AWS vulnerable lab para practicar.

### Azure

- **AzureHound**: BloodHound para Azure AD.
- **MicroBurst**: scripts PowerShell pentest Azure.
- **ROADtools**: enumeración Azure AD.

### GCP

- **GCP Goat**: GCP vulnerable lab.

## Frameworks y compliance

- **CIS Benchmarks**: hardening guides para cada cloud.
- **AWS Well-Architected Framework — Security Pillar**.
- **Azure Security Benchmark**.
- **NIST 800-53** mapeado a AWS (vía AWS Security Hub).
- **SOC 2**, **ISO 27001**, **PCI-DSS**: compliance comercial.

## Cloud-native security tools

### CSPM (Cloud Security Posture Management)

Detectan misconfiguraciones continuamente:
- **Prisma Cloud** (Palo Alto)
- **Wiz**, **Lacework**, **Orca Security**
- **AWS Security Hub**, **Azure Defender for Cloud**

### CWPP (Cloud Workload Protection Platform)

Protección de workloads (VMs, containers):
- **Sysdig Secure**, **Aqua Security**, **Snyk**

### CIEM (Cloud Infrastructure Entitlement Management)

Analiza permisos IAM (least privilege):
- **Sonrai**, **Authomize**, **Microsoft Entra Permissions**

### SIEM cloud-native

- **AWS Security Lake** + **Athena**.
- **Microsoft Sentinel** (cloud-native SIEM).
- **Google Chronicle**.

## Container security (subdominio)

### Docker/Kubernetes

- **kubectl auth can-i** — qué permisos tengo en k8s.
- **kube-bench** — CIS Benchmark de k8s.
- **kube-hunter** — pentest de k8s clusters.
- **Trivy** — scanner de imágenes Docker.

### Vulns comunes en containers

- Containers con `privileged: true`.
- HostPath mount de `/`.
- Secrets en environment variables.
- Images con vulnerabilidades sin patch.

## Cobertura en el vault

- [[_4- Endurecimiento de las nubes|Curso Google Cyber 3 → Endurecimiento de las nubes]] —
  fundamentos cloud security.
- [[_5- Curso de Docker Aplicado a la Ciberseguridad|5- Docker para Ciberseguridad]] —
  _(pendiente, ver roadmap)_.

## Estrategia de aprendizaje (recomendación)

1. **Fundamentos cloud**: AWS Solutions Architect Associate (entender el
   ecosistema).
2. **AWS Security Specialty** (o Azure SC-100, GCP Cloud Security Engineer).
3. **HackTheBox Cloud Path** o **CloudGoat** para práctica.
4. **CCSP** ((ISC)²) como certificación general.

## Certificaciones cloud security

- **AWS Security Specialty** — la más demandada.
- **Azure SC-100 / SC-200**.
- **GCP Professional Cloud Security Engineer**.
- **CCSP** (Certified Cloud Security Professional, (ISC)²).
- **CCSK** (Cloud Security Alliance).

## Aspectos legales / contractuales

- AWS, Azure, GCP **requieren autorización previa** para pentest en algunos
  servicios (ya no en la mayoría, pero leer la "Acceptable Use Policy").
- **Bug bounty**: AWS Vulnerability Reporting, Azure Bounty, Google VRP.

## Navegación

- 🏠 [[🔒🐧Hub|Hub Principal del vault]]
- [[index|Index general del vault]]

## Relacionadas

- [[MOC - Pentesting end-to-end|MOC - Pentesting]] — el flujo aplicado a cloud.
- [[MOC - Web Pentesting OWASP|MOC - OWASP]] — A10 SSRF afecta cloud metadata.
- [[Authentication|Authentication]] — IAM es authentication en cloud.
- [[Networking|Networking]] — VPC, security groups, NACLs.
- [[Pentesting|Pentesting]] — concepto general aplicado a cloud.
