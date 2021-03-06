---
layout: "oci"
page_title: "OCI: oci_identity_auth_token"
sidebar_current: "docs-oci-resource-identity-auth_token"
description: |-
  Creates and manages an OCI AuthToken
---

# oci_identity_auth_token
The `oci_identity_auth_token` resource creates and manages an OCI AuthToken

Creates a new auth token for the specified user. For information about what auth tokens are for, see
[Managing User Credentials](https://docs.us-phoenix-1.oraclecloud.com/Content/Identity/Tasks/managingcredentials.htm).

You must specify a *description* for the auth token (although it can be an empty string). It does not
have to be unique, and you can change it anytime with
[UpdateAuthToken](https://docs.us-phoenix-1.oraclecloud.com/api/#/en/identity/20160918/AuthToken/UpdateAuthToken).

Every user has permission to create an auth token for *their own user ID*. An administrator in your organization
does not need to write a policy to give users this ability. To compare, administrators who have permission to the
tenancy can use this operation to create an auth token for any user, including themselves.


## Example Usage

```hcl
resource "oci_identity_auth_token" "test_auth_token" {
	#Required
	description = "${var.auth_token_description}"
	user_id = "${oci_identity_user.test_user.id}"
}
```

## Argument Reference

The following arguments are supported:

* `description` - (Required) (Updatable) The description you assign to the auth token during creation. Does not have to be unique, and it's changeable. 


** IMPORTANT **
Any change to a property that does not support update will force the destruction and recreation of the resource with the new property values

## Attributes Reference

The following attributes are exported:

* `description` - The description you assign to the auth token. Does not have to be unique, and it's changeable.
* `id` - The OCID of the auth token.
* `inactive_state` - The detailed status of INACTIVE lifecycleState.
* `state` - The token's current state. After creating an auth token, make sure its `lifecycleState` changes from CREATING to ACTIVE before using it. 
* `time_created` - Date and time the `AuthToken` object was created, in the format defined by RFC3339.  Example: `2016-08-25T21:10:29.600Z` 
* `time_expires` - Date and time when this auth token will expire, in the format defined by RFC3339. Null if it never expires.  Example: `2016-08-25T21:10:29.600Z` 
* `token` - The auth token. The value is available only in the response for `CreateAuthToken`, and not for `ListAuthTokens` or `UpdateAuthToken`. 
* `user_id` - The OCID of the user the auth token belongs to.
