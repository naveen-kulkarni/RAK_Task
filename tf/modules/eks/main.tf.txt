resource "aws_eks_cluster" "this" {
  name = var.cluster_name
  version = var.cluster_version
  role_arn = var.cluster_role_arn
  vpc_config {
    subnet_ids = var.subnets
  }

  depends_on = [aws_iam_role_policy_attachment.eks_cluster_policy]
}

resource "aws_eks_node_group" "this" {
  cluster_name = aws_eks_cluster.this.name
  node_group_name = "${var.cluster_name}-nodes"
  node_role_arn = var.node_role_arn
  subnets = var.subnets

  scaling_config {
    desired_size = var.desired_capacity
    max_size = var.max_capacity
    min_size = var.min_capacity
  }

  instance_types = [var.node_instance_type]
  ami_type = "AL2_x86_64"
}
