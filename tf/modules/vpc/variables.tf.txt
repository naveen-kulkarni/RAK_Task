variable "cidr_block" {
  description = "The CIDR block for the VPC"
  type = string
}

variable "name" {
  description = "The name of the VPC"
  type = string
}

variable "azs" {
  description = "The availability zones"
  type = list(string)
}

variable "public_subnets" {
  description = "The public subnets"
  type = list(string)
}

variable "private_subnets" {
  description = "The private subnets"
  type = list(string)
}
