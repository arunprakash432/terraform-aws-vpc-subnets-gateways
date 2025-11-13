
---

# 🚀 AWS VPC Terraform Setup

This project provides a **minimal Terraform configuration** that deploys the following AWS networking components:

## 📦 What This Terraform Code Creates

* **VPC** (10.0.0.0/16)
* **4 Subnets**

  * 2 Public (1 per AZ)
  * 2 Private (1 per AZ)
* **Internet Gateway (IGW)**
* **Public Route Table**

  * Default route → IGW
* **Private Route Table**

  * S3 access through **Gateway VPC Endpoint**
* **S3 Gateway Endpoint** for private subnet access without NAT
* Clean outputs: VPC ID, subnet IDs, S3 endpoint ID

All components are intentionally minimal and easy to extend.

---

## 📁 Project Structure

```
.
├── main.tf
├── providers.tf
├── variables.tf
├── outputs.tf
└── README.md
```

---

## 🛠️ Requirements

* **Terraform ≥ 1.0.0**
* **AWS CLI** configured with credentials
* An AWS account with permissions to create:

  * VPCs
  * Subnets
  * Route tables
  * Internet gateways
  * VPC endpoints

---

## ▶️ How to Use

### 1. Initialize Terraform

```sh
terraform init
```

### 2. Review the execution plan

```sh
terraform plan
```

### 3. Apply (deploy resources)

```sh
terraform apply
```

### 4. Destroy (remove resources)

```sh
terraform destroy
```

---

## 📝 Variables

| Variable | Description                         | Default     |
| -------- | ----------------------------------- | ----------- |
| `region` | AWS region to deploy resources into | `ap-south-1` |

You can override the region:

```sh
terraform apply -var="region=eu-west-1"
```

---

## 📤 Outputs

After deployment Terraform prints:

* **VPC ID**
* **Public Subnet IDs**
* **Private Subnet IDs**
* **S3 VPC Endpoint ID**

Example:

```
vpc_id = vpc-1234567890abcdef
public_subnets = [subnet-aaa, subnet-bbb]
private_subnets = [subnet-ccc, subnet-ddd]
s3_vpc_endpoint_id = vpce-123abc456def
```

---

