---
layout: "ibm"
page_title: "IBM : ibm_cd_toolchain_tool_custom"
description: |-
  Manages cd_toolchain_tool_custom.
subcategory: "CD Toolchain"
---

# ibm_cd_toolchain_tool_custom

~> **Beta:** This resource is in Beta, and is subject to change.

Provides a resource for cd_toolchain_tool_custom. This allows cd_toolchain_tool_custom to be created, updated and deleted.

## Example Usage

```hcl
resource "ibm_cd_toolchain_tool_custom" "cd_toolchain_tool_custom" {
  parameters {
		type = "type"
		lifecycle_phase = "THINK"
		image_url = "imageUrl"
		documentation_url = "documentationUrl"
		name = "name"
		dashboard_url = "dashboard_url"
		description = "description"
		additional_properties = "additional-properties"
  }
  toolchain_id = "toolchain_id"
}
```

## Argument Reference

Review the argument reference that you can specify for your resource.

* `name` - (Optional, String) Name of tool.
  * Constraints: The maximum length is `128` characters. The minimum length is `0` characters. The value must match regular expression `/^([^\\x00-\\x7F]|[a-zA-Z0-9-._ ])+$/`.
* `parameters` - (Required, List) Parameters to be used to create the tool.
Nested scheme for **parameters**:
	* `additional_properties` - (Optional, String) (Advanced) Type any information that is needed to integrate with other tools in your toolchain.
	* `dashboard_url` - (Required, String) Type the URL that you want to navigate to when you click the tool integration card.
	* `description` - (Optional, String) Type a description for the tool instance.
	* `documentation_url` - (Optional, String) Type the URL for your tool's documentation.
	* `image_url` - (Optional, String) Type the URL of the icon to show on your tool integration's card.
	* `lifecycle_phase` - (Required, String) Select the lifecycle phase of the IBM Cloud Garage Method that is the most closely associated with this tool.
	  * Constraints: Allowable values are: `THINK`, `CODE`, `DELIVER`, `RUN`, `MANAGE`, `LEARN`, `CULTURE`.
	* `name` - (Required, String) Type a name for this specific tool integration; for example: My Build and Deploy Pipeline.
	* `type` - (Required, String) Type the name of the tool that you are integrating; for example: Delivery Pipeline.
* `toolchain_id` - (Required, Forces new resource, String) ID of the toolchain to bind tool to.
  * Constraints: The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/^[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-4[a-fA-F0-9]{3}-[89abAB][a-fA-F0-9]{3}-[a-fA-F0-9]{12}$/`.

## Attribute Reference

In addition to all argument references listed, you can access the following attribute references after your resource is created.

* `id` - The unique identifier of the cd_toolchain_tool_custom.
* `crn` - (String) Tool CRN.
* `tool_id` - (String) Tool ID.
  * Constraints: The maximum length is `36` characters. The minimum length is `36` characters. The value must match regular expression `/^[a-fA-F0-9]{8}-[a-fA-F0-9]{4}-4[a-fA-F0-9]{3}-[89abAB][a-fA-F0-9]{3}-[a-fA-F0-9]{12}$/`.
* `href` - (String) URI representing the tool.
* `referent` - (List) Information on URIs to access this resource through the UI or API.
Nested scheme for **referent**:
	* `api_href` - (String) URI representing the this resource through an API.
	* `ui_href` - (String) URI representing the this resource through the UI.
* `resource_group_id` - (String) Resource group where tool can be found.
* `state` - (String) Current configuration state of the tool.
  * Constraints: Allowable values are: `configured`, `configuring`, `misconfigured`, `unconfigured`.
* `toolchain_crn` - (String) CRN of toolchain which the tool is bound to.
* `updated_at` - (String) Latest tool update timestamp.

## Provider Configuration

The IBM Cloud provider offers a flexible means of providing credentials for authentication. The following methods are supported, in this order, and explained below:

- Static credentials
- Environment variables

To find which credentials are required for this resource, see the service table [here](https://cloud.ibm.com/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-provider-reference#required-parameters).

### Static credentials

You can provide your static credentials by adding the `ibmcloud_api_key`, `iaas_classic_username`, and `iaas_classic_api_key` arguments in the IBM Cloud provider block.

Usage:
```
provider "ibm" {
    ibmcloud_api_key = ""
    iaas_classic_username = ""
    iaas_classic_api_key = ""
}
```

### Environment variables

You can provide your credentials by exporting the `IC_API_KEY`, `IAAS_CLASSIC_USERNAME`, and `IAAS_CLASSIC_API_KEY` environment variables, representing your IBM Cloud platform API key, IBM Cloud Classic Infrastructure (SoftLayer) user name, and IBM Cloud infrastructure API key, respectively.

```
provider "ibm" {}
```

Usage:
```
export IC_API_KEY="ibmcloud_api_key"
export IAAS_CLASSIC_USERNAME="iaas_classic_username"
export IAAS_CLASSIC_API_KEY="iaas_classic_api_key"
terraform plan
```

Note:

1. Create or find your `ibmcloud_api_key` and `iaas_classic_api_key` [here](https://cloud.ibm.com/iam/apikeys).
  - Select `My IBM Cloud API Keys` option from view dropdown for `ibmcloud_api_key`
  - Select `Classic Infrastructure API Keys` option from view dropdown for `iaas_classic_api_key`
2. For iaas_classic_username
  - Go to [Users](https://cloud.ibm.com/iam/users)
  - Click on user.
  - Find user name in the `VPN password` section under `User Details` tab

For more informaton, see [here](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs#authentication).

## Import

You can import the `ibm_cd_toolchain_tool_custom` resource by using `id`.
The `id` property can be formed from `toolchain_id`, and `tool_id` in the following format:

```
<toolchain_id>/<tool_id>
```
* `toolchain_id`: A string. ID of the toolchain to bind tool to.
* `tool_id`: A string. ID of the tool bound to the toolchain.

# Syntax
```
$ terraform import ibm_cd_toolchain_tool_custom.cd_toolchain_tool_custom <toolchain_id>/<tool_id>
```
