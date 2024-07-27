variable "cluster_name" {
  description = "The name of the EKS cluster"
  type = string
}

variable "cluster_version" {
  description = "The version of the EKS cluster"
  type = string
}

variable "subnets" {
  description = "The subnets for the EKS cluster"
  type = list(string)
}

variable "cluster_role_arn" {
  description = "The ARN of the IAM role for the EKS cluster"
  type = string
}

variable "node_role_arn" {
  description = "The ARN of the IAM role for the worker nodes"
  type = string
}

variable "node_instance_type" {
  description = "The instance type for the worker nodes"
  type = string
}

variable "desired_capacity" {
  description = "The desired capacity of the node group"
  type = number
}

variable "max_capacity" {
  description = "The maximum capacity of the node group"
  type = number
}

variable "min_capacity" {
  description = "The minimum capacity of the node group"
  type = number
}
