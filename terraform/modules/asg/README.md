## Terraform module for creating ALB


## Usage

### Application Load Balancer

HTTP and HTTPS listeners with default actions:

```hcl
module "alb" {
  source  = "modules/alb"
  
  name = "my-alb"

  load_balancer_type = "application"

  vpc_id             = "vpc-abcde012"
  subnets            = ["subnet-abcde012","subnet-bcde012a"]
  security_groups    = ["sg-edcd9784", "sg-edcd9785"]
  
  access_logs = {
    enabled = true
    bucket = "my-alb-logs"
  }

  tags = {
    Environment = "Test"
  }
}
```

<!-- BEGINNING OF OUTPUT FROM terraform-docs plugin -->
<!-- Command used terraform-docs md table . > README.md -->
<!-- Reference : https://github.com/terraform-docs/terraform-docs -->


## Requirements

| Name | Version |      
|------|---------|      
| terraform | = 0.13.4 |
| aws | ~> 3.8.0 |      

## Providers

| Name | Version |      
|------|---------|      
| aws | ~> 3.8.0 |      
| tls | n/a |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| alb\_name | The resource name and Name tag of the load balancer. | `string` | `"alb-01"` | no |
| alb\_sg\_id | SG ID of ALB | `list(string)` | n/a | yes |
| ami\_id | Enter the ami id of a  centos machine | `string` | n/a | yes |
| asg\_name | Name of ASG | `string` | `"asg-01"` | no |
| asg\_tags | Tags for ASG instances | `map(string)` | <pre>{<br>  "Name": "asg-ec2",<br>  "type": "app"<br>}</pre> | no |
| azs | List of AZ | `list(string)` | <pre>[<br>  "us-west-2a",<br>  "us-west-2b"<br>]</pre> | no |
| desired\_instance\_count | Min instance count | `number` | `1` | no |
| drop\_invalid\_header\_fields | Indicates whether invalid header fields are dropped in application load balancers. Defaults to false. | `bool` | `false` | no |
| ec2\_sg\_id | SG ID of EC2 | `list(string)` | n/a | yes |
| elb\_tags | A map of tags to add to all resources | `map(string)` | <pre>{<br>  "classificaton": "internal/sensitive"<br>}</pre> | no |
| enable\_cross\_zone\_load\_balancing | Indicates whether cross zone load balancing should be enabled in application load balancers. | `bool` | `false` | no |
| enable\_deletion\_protection | If true, deletion of the load balancer will be disabled via the AWS API. This will prevent Terraform from deleting the load balancer. Defaults to false. | `bool` | `false` | no |
| enable\_http2 | Indicates whether HTTP/2 is enabled in application load balancers. | `bool` | `true` | no |
| health\_check | Health check settings | `list(map(string))` | <pre>[<br>  {<br>    "path": "/",<br>    "port": "traffic-port",<br>   
 "protocol": "HTTP"<br>  }<br>]</pre> | no |
| health\_check\_type | Type of health check | `string` | `""` | no |
| http\_listener\_port | Listener port for HTTP | `number` | `80` | no |
| http\_listener\_protocol | Listener protocol | `string` | `"HTTP"` | no |
| iam\_role\_tags | Tags for IAM role | `map(string)` | <pre>{<br>  "Name": "instance-role"<br>}</pre> | no |
| idle\_timeout | The time in seconds that the connection is allowed to be idle. | `number` | `60` | no |
| instance\_access\_policy\_name | Name of the Instance IAM access policy | `string` | `"instance-access-policy"` | no |
| instance\_profile\_name | Name of the Instance IAM profile | `string` | `"instance-profile"` | no |
| instance\_role\_name | Name of the Instance IAM role | `string` | `"instance-role"` | no |
| instance\_type | Type of instance | `string` | `"t2.micro"` | no |
| ip\_address\_type | The type of IP addresses used by the subnets for your load balancer. The possible values are ipv4 and dualstack. 
| `string` | `"ipv4"` | no |
| is\_internal | is ALB internal | `bool` | `false` | no |
| key\_pair\_name | Name of instance key pair | `string` | `"usw2_keypair"` | no |
| lc\_name | Name of launch configuration | `string` | `"lcv-01"` | no |
| load\_balancer\_type | The type of load balancer to create. Possible values are application or network. | `string` | `"application"` 
| no |
| max\_instance\_count | Max instance count | `number` | `1` | no |
| min\_instance\_count | Min instance count | `number` | `1` | no |
| private\_subnet\_ids | List of private subnet IDS | `list(string)` | `[]` | no |
| subnets\_id\_list | A list of subnets to associate with the load balancer. e.g. ['subnet-1a2b3c4d','subnet-1a2b3c4e','subnet-1a2b3c4f'] | `list(string)` | `null` | no |
| target\_group\_name | The resource name and Name tag of the TG | `string` | `"tg-01"` | no |
| target\_group\_port | Port of TG | `number` | `80` | no |
| target\_group\_protocol | Protocol of TG | `string` | `"HTTP"` | no |
| target\_group\_tags | Tags for the target group | `map(string)` | <pre>{<br>  "tier": "public"<br>}</pre> | no |
| vpc\_id | Enter the VPC ID | `string` | n/a | yes |

## Outputs

| Name | Description |
|------|-------------|
| private\_key | n/a |
| this\_lb\_arn | The ID and ARN of the load balancer we created. |
| this\_lb\_dns\_name | The DNS name of the load balancer. |
| this\_lb\_id | The ID and ARN of the load balancer we created. |

<!-- END OF OUTPUT FROM terra-docs -->

## Reference
https://github.com/terraform-aws-modules/terraform-aws-alb/blob/master/main.tf
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/lb#allocation_id

## Authors
Dharani Sowndharya
