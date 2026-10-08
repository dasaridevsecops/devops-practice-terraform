### Multi-Cloud Terraform Import (AWS, Azure & GCP)

1. Prepare resource block

Example
```
AWS

resource "aws_instance" "example" {
    ami           = "ami-0220d79f3f480ecf5"
    instance_type = "t3.micro"

    tags = {
        Name = "terraform-import"
    }
}
```
```
Azure

provider "azurerm" {
  features {}
}

resource "azurerm_resource_group" "demo" {
  name     = "my-existing-rg"
  location = "East US"
}
```
```
GCP

provider "google" {
  project = "my-gcp-project"
  region  = "us-central1"
}

resource "google_compute_instance" "web" {
  name         = "web-server-01"
  machine_type = "e2-medium"
  zone         = "us-central1-a"
  boot_disk {
    initialize_params {
      image = "debian-cloud/debian-12"
    }
  }

  network_interface {
    network = "default"
  }
}
```

2. Run plan
```
terraform plan
plan: 1 to add, 0 to change, 0 to destroy
```
3. Run terraform import
```
terraform import aws_instance.example <resource_id>
```
```
terraform import azurerm_resource_group.existing_rg /subscriptions/<subscription_id>/resourceGroups/<resource_group_name>
```

```
 terraform import google_compute_instance.web projects/my-gcp-project/zones/us-central1-a/instances/web-server-01
```
Import Successful. <br/>
4. Apply plan again
```
terraform plan
```
No changes. Your infrastructure matches the configuration.
