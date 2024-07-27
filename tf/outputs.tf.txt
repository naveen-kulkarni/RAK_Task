output "shared_logging_bucket" {
  description = "The name of the shared logging bucket"
  value       = aws_s3_bucket.logging.bucket
}

output "common_policy_arn" {
  description = "The ARN of the common IAM policy"
  value       = aws_iam_policy.common_policy.arn
}

