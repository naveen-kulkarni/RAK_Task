variable "region" {
  description = "The AWS region to deploy resources"
  type        = string
  default     = "us-west-2"
}

variable "common_tags" {
  description = "A map of tags to apply to all resources"
  type        = map(string)
  default     = {
    Environment = "shared"
    Project     = "MyProject"
  }
}
