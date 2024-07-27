provider "aws" {
  region = var.region
}

# Shared S3 bucket for logging, if needed
resource "aws_s3_bucket" "logging" {
  bucket = "my-shared-logging-bucket"
  acl    = "private"

  versioning {
    enabled = true
  }

  lifecycle_rule {
    enabled = true
    transition {
      days          = 30
      storage_class = "STANDARD_IA"
    }
    expiration {
      days = 365
    }
  }

  tags = {
    Name        = "shared-logging-bucket"
    Environment = "shared"
  }
}

# Example of a shared IAM policy
resource "aws_iam_policy" "common_policy" {
  name        = "common-policy"
  description = "A common policy used by multiple environments"
  policy      = jsonencode({
    Version = "2012-10-17"
    Statement = [
      {
        Action = [
          "s3:ListBucket",
          "s3:GetObject"
        ]
        Effect   = "Allow"
        Resource = [
          "arn:aws:s3:::my-shared-logging-bucket",
          "arn:aws:s3:::my-shared-logging-bucket/*"
        ]
      }
    ]
  })
}
