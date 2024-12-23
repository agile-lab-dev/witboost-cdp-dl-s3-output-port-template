## Using the template

### Prerequisites

A Data Product should already exist in order to attach the new components to it.

---

### Registering the template on the product

To register the template to Witboost and start creating components with it, follow the steps below:

- Go to Builder > Templates
- Click "Register Existing Component"
- Give the url of `template.yaml` file in the url field and click Analyze
- Click Import to import this template

### Component Basic Information

This section includes the basic information that any component of Witboost must have.

- Name: Required name used for display purposes on your Data Product.
- Description: A short description to help others understand what this Output Port is for.
- Domain: The Domain of the Data Product this Output Port belongs to. Be sure to choose it correctly as is a fundamental part of the Output Port and cannot be changed afterward.
- Data Product: The Data Product this Output Port belongs to, be sure to choose the right one.
- Identifier: Unique ID for this new entity inside the domain. Don't worry to fill this field, it will be automatically filled for you.
- Development Group: Development group of this Data Product. Don't worry to fill this field, it will be automatically filled for you.
- Depends On: If you want your Output Port to depend on other components from the Data Product, you can choose this option.

*Example:*

| Field name              | Example value                                                                                          |
|:------------------------|:-------------------------------------------------------------------------------------------------------|
| **Name**                | S3 CDP Output Port                                                                                     |
| **Description**         | Offers insight in some data leveraging CDP Impala                                                      |
| **Domain**              | domain:finance                                                                                         |
| **Data Product**        | system:finance.cashflow.0                                                                              |
| ***Identifier***        | Will look something like this: *finance.cashflow.0.s3-cdp-output-port*                                 |
| ***Development Group*** | Might look something like this: *group:datameshplatform* Depends on the Data Product development group |

### Provide some additional information

This section includes additional information about the component, including fields that will be included in the output port data contract.

- Process Description: What is the underlying process that contributes to generate the data exposed by this output port
- Interval of change: How often changes in the data are reflected
- Timeliness: The skew between the time that a business fact occurs and when it becomes visible in the data
- Uptime: The percentage of port availability
- Terms and conditions: If the data is usable only in specific environments
- Endpoint: This is the API endpoint that self-describe the output port and provide insightful information at runtime about the physical location of the data, the protocol must be used, etc.

| Field name               | Example value |
|:-------------------------|:--------------|
| **Process Description**  | example       |
| **Interval of change**   | example       |
| **Timeliness**           | example       |
| **Uptime**               | example       |
| **Terms and conditions** | example       |
| **Endpoint**             | example       |

### Data sharing agreements information

This section includes information about the data sharing agreement field included in the Output Port, defining the expected way to utilize the information provided by this Output Port in terms of billing, security, intended usage, etc.

- Purpose: What is the goal of this data set
- Billing: How a consumer will be charged back when it consumes this output port
- Security: Additional information related to security aspects, like restrictions, maskings, sensible information and privacy
- IntendedUsage: Any other information needed by the consumer in order to effectively consume the data, it could be related to technical stuff (e.g. extract no more than one year of data for good performances ) or to business domains (e.g. this data is only useful in the marketing domains)
- Limitations: If any limitation is present it must be made super clear to the consumers
- LifeCycle: Describe how the data will be historicized and how and when it will be deleted
- Confidentiality: Describe what a consumer should do to keep the information confidential, how to process and store it. Permission to share or report it

| Field name          | Example value |
|:--------------------|:--------------|
| **Purpose**         | example       |
| **Billing**         | example       |
| **Security**        | example       |
| **Intended Usage**  | example       |
| **Limitations**     | example       |
| **Lifecycle**       | example       |
| **Confidentiality** | example       |

### Provide Output port deployment information

This section includes information about the location of the deployed data used by the Output Port to access and expose it.

- CDP Environment: Name of the CDP Environment
- Bucket: Name of the S3 bucket. Valid buckets are the same configured on the CDP Environment
- Folder: Name of the Folder key in the S3 bucket. Valid values must start with mesh/domains/$Domain/data-products/$DataProductName/$Environment/$DataProductVersion/

| Field name          | Example value                                                          |
|:--------------------|:-----------------------------------------------------------------------|
| **CDP Environment** | my-cdp-env                                                             |
| **Bucket**          | my-cdp-bucket                                                          |
| **Folder**          | mesh/domains/finance/data-products/cashflow_0/development/0/my-folder/ |

## After creation

In order to customize the component information, access the component repository and update the `spec.mesh` section inside the `catalog-info.yaml` according to the [Data Product specification](https://github.com/agile-lab-dev/Data-Product-Specification) and to the `CDP S3 Tech Adapter contract`.