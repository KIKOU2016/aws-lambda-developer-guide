# AddLayerVersionPermission<a name="API_AddLayerVersionPermission"></a>

Adds permissions to the resource\-based policy of a version of an [AWS Lambda layer](https://docs.aws.amazon.com/lambda/latest/dg/configuration-layers.html)\. Use this action to grant layer usage permission to other accounts\. You can grant permission to a single account, all AWS accounts, or all accounts in an organization\.

To revoke permission, call [RemoveLayerVersionPermission](API_RemoveLayerVersionPermission.md) with the statement ID that you specified when you added it\.

## Request Syntax<a name="API_AddLayerVersionPermission_RequestSyntax"></a>

```
POST /2018-10-31/layers/LayerName/versions/VersionNumber/policy?RevisionId=RevisionId HTTP/1.1
Content-type: application/json

{
   "[Action](#SSS-AddLayerVersionPermission-request-Action)": "string",
   "[OrganizationId](#SSS-AddLayerVersionPermission-request-OrganizationId)": "string",
   "[Principal](#SSS-AddLayerVersionPermission-request-Principal)": "string",
   "[StatementId](#SSS-AddLayerVersionPermission-request-StatementId)": "string"
}
```

## URI Request Parameters<a name="API_AddLayerVersionPermission_RequestParameters"></a>

The request requires the following URI parameters\.

 ** [LayerName](#API_AddLayerVersionPermission_RequestSyntax) **   <a name="SSS-AddLayerVersionPermission-request-LayerName"></a>
The name or Amazon Resource Name \(ARN\) of the layer\.  
Length Constraints: Minimum length of 1\. Maximum length of 140\.  
Pattern: `(arn:[a-zA-Z0-9-]+:lambda:[a-zA-Z0-9-]+:\d{12}:layer:[a-zA-Z0-9-_]+)|[a-zA-Z0-9-_]+` 

 ** [RevisionId](#API_AddLayerVersionPermission_RequestSyntax) **   <a name="SSS-AddLayerVersionPermission-request-RevisionId"></a>
Only update the policy if the revision ID matches the ID specified\. Use this option to avoid modifying a policy that has changed since you last read it\.

 ** [VersionNumber](#API_AddLayerVersionPermission_RequestSyntax) **   <a name="SSS-AddLayerVersionPermission-request-VersionNumber"></a>
The version number\.

## Request Body<a name="API_AddLayerVersionPermission_RequestBody"></a>

The request accepts the following data in JSON format\.

 ** [Action](#API_AddLayerVersionPermission_RequestSyntax) **   <a name="SSS-AddLayerVersionPermission-request-Action"></a>
The API action that grants access to the layer\. For example, `lambda:GetLayerVersion`\.  
Type: String  
Pattern: `lambda:GetLayerVersion`   
Required: Yes

 ** [OrganizationId](#API_AddLayerVersionPermission_RequestSyntax) **   <a name="SSS-AddLayerVersionPermission-request-OrganizationId"></a>
With the principal set to `*`, grant permission to all accounts in the specified organization\.  
Type: String  
Pattern: `o-[a-z0-9]{10,32}`   
Required: No

 ** [Principal](#API_AddLayerVersionPermission_RequestSyntax) **   <a name="SSS-AddLayerVersionPermission-request-Principal"></a>
An account ID, or `*` to grant permission to all AWS accounts\.  
Type: String  
Pattern: `\d{12}|\*|arn:(aws[a-zA-Z-]*):iam::\d{12}:root`   
Required: Yes

 ** [StatementId](#API_AddLayerVersionPermission_RequestSyntax) **   <a name="SSS-AddLayerVersionPermission-request-StatementId"></a>
An identifier that distinguishes the policy from others on the same layer version\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 100\.  
Pattern: `([a-zA-Z0-9-_]+)`   
Required: Yes

## Response Syntax<a name="API_AddLayerVersionPermission_ResponseSyntax"></a>

```
HTTP/1.1 201
Content-type: application/json

{
   "[RevisionId](#SSS-AddLayerVersionPermission-response-RevisionId)": "string",
   "[Statement](#SSS-AddLayerVersionPermission-response-Statement)": "string"
}
```

## Response Elements<a name="API_AddLayerVersionPermission_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 201 response\.

The following data is returned in JSON format by the service\.

 ** [RevisionId](#API_AddLayerVersionPermission_ResponseSyntax) **   <a name="SSS-AddLayerVersionPermission-response-RevisionId"></a>
A unique identifier for the current revision of the policy\.  
Type: String

 ** [Statement](#API_AddLayerVersionPermission_ResponseSyntax) **   <a name="SSS-AddLayerVersionPermission-response-Statement"></a>
The permission statement\.  
Type: String

## Errors<a name="API_AddLayerVersionPermission_Errors"></a>

 **InvalidParameterValueException**   
One of the parameters in the request is invalid\. For example, if you provided an IAM role for AWS Lambda to assume in the `CreateFunction` or the `UpdateFunctionConfiguration` API, that AWS Lambda is unable to assume you will get this exception\.  
HTTP Status Code: 400

 **PolicyLengthExceededException**   
The permissions policy for the resource is too large\. [Learn more](https://docs.aws.amazon.com/lambda/latest/dg/limits.html)   
HTTP Status Code: 400

 **PreconditionFailedException**   
The RevisionId provided does not match the latest RevisionId for the Lambda function or alias\. Call the `GetFunction` or the `GetAlias` API to retrieve the latest RevisionId for your resource\.  
HTTP Status Code: 412

 **ResourceConflictException**   
The resource already exists\.  
HTTP Status Code: 409

 **ResourceNotFoundException**   
The resource \(for example, a Lambda function or access policy statement\) specified in the request does not exist\.  
HTTP Status Code: 404

 **ServiceException**   
The AWS Lambda service encountered an internal error\.  
HTTP Status Code: 500

 **TooManyRequestsException**   
Request throughput limit exceeded\.  
HTTP Status Code: 429

## See Also<a name="API_AddLayerVersionPermission_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/lambda-2015-03-31/AddLayerVersionPermission) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/lambda-2015-03-31/AddLayerVersionPermission) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/lambda-2015-03-31/AddLayerVersionPermission) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/lambda-2015-03-31/AddLayerVersionPermission) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/lambda-2015-03-31/AddLayerVersionPermission) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/lambda-2015-03-31/AddLayerVersionPermission) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/lambda-2015-03-31/AddLayerVersionPermission) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/lambda-2015-03-31/AddLayerVersionPermission) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/lambda-2015-03-31/AddLayerVersionPermission) 