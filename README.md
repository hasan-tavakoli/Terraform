# Google Cloud Composer Terraform Configuration

This repository contains a Terraform configuration for setting up a Google Cloud Composer environment. The configuration includes service account permissions, environment setup, and network configurations for the Composer environment.

## Overview

The Terraform script sets up a Google Cloud Composer environment with various configurations, including:

- Enabling the Composer API
- Configuring IAM roles for the Composer service account
- Setting up the Composer environment with network and software configurations
- Managing private environment settings and maintenance windows

## Configuration Details

### Data Sources

- **`google_project`**: Retrieves project details required for configuring the Composer environment and service accounts.

### Local Variables

- **`cloud_composer_sa`**: Constructs the service account email for Cloud Composer.
- **`master_authorized_networks_config`**: Configures the list of authorized networks for the Composer environment.

### Resources

1. **`google_project_service`**:
   - **Purpose**: Enables the Cloud Composer API for the specified project.
   - **Service**: `composer.googleapis.com`

2. **`google_service_account_iam_member`**:
   - **Purpose**: Grants the `roles/composer.ServiceAgentV2Ext` role to the Composer service account.
   - **Service Account**: Constructed using the project number and `composer_service_account` variable.

3. **`google_composer_environment`**:
   - **Purpose**: Configures a Cloud Composer environment with various settings.
   - **Parameters**:
     - `project`: The Google Cloud project ID
     - `name`: The name of the Composer environment
     - `region`: The region for the environment
     - `labels`: Labels for the environment
     - `config`: Configuration details including environment size, node configuration, software configuration, private environment settings, and maintenance windows
     - `workloads_config`: Configures the resources for scheduler, web server, and worker workloads
     - `master_authorized_networks_config`: Configures authorized networks for the environment

### Directory Structure

The main components of the configuration include:

- **Service Account IAM Setup**: Grants necessary permissions for Cloud Composer.
- **Environment Configuration**: Sets up the Composer environment with various dynamic configurations for networking, software, and workload settings.
