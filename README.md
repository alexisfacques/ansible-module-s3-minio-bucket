# ansible-module-minio-bucket

`ansible-module-minio-bucket` is a custom Ansible module allowing you to create
and delete MinIO S3 buckets. It is roughly similar to
[s3_bucket](s3_bucket_module) and [aws_s3](aws_s3_module), but **it supports
MinIO bucket policies**.

## Getting started

### Requirements

The below requirements are needed **on the host that execute** this module.

- `minio` for Python.

### Installing

#### The "Ansible role" way

- Clone this repository to your Ansible `role_path`, or install via
`ansible-galaxy`;
  ```sh
  ansible-galaxy install alexisfacques.ansible_module_minio_bucket
  ```
- Import the role in your playbooks before running any role or task that
require the `minio_bucket` module:
  ```yaml
  - hosts: all
    roles:
      - alexisfacques.ansible_module_minio_bucket
    tasks:
      - minio_bucket:
          ...
  ```

#### The "Ansible library" way

Alternatively, if importing a role is too much of a hassle, you can store this
module in the `library` directory defined in your `ansible.cfg` file
(Default is a sub-directory called `library` in the directory that contains
your playbooks):
```
[defaults]
library = /path/to/your/library
```

## Usage

### Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Choices/Defaults</th>
    <th>Comments</th>
  </tr>
  <tr>
    <td>s3_url<br>- string / required</td>
    <td></td>
    <td>S3 URL endpoint.</td>
  </tr>
  <tr>
    <td>name<br>- string / required</td>
    <td></td>
    <td>Name of the S3 bucket.</td>
  </tr>
  <tr>
    <td>access_key<br>- string / required</td>
    <td></td>
    <td>MinIO S3 access key.</td>
  </tr>
  <tr>
    <td>secret_key<br>- string / required</td>
    <td></td>
    <td>MinIO S3 secret key.</td>
  </tr>
  <tr>
    <td>state<br></td>
    <td>Choices:<br><strong>present</strong> / absent</td>
    <td>Create or remove the S3 bucket.</td>
  </tr>
  <tr>
    <td>policy<br></td>
    <td>Choices:<br><strong>private (leave empty)</strong> / read-only /
    write-only / read-write </td>
    <td>MinIO S3 bucket policy.</td>
  </tr>
  <tr>
    <td>validate_certs<br>boolean /</td>
    <td>Choices:<br><strong>yes</strong> / no</td>
    <td>When set to "no", SSL certificates will not be validated for boto
    versions >= 2.6.0.</td>
  </tr>
</table>

### Example of use

Examples of use can be found [here](./examples/demo.yml).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE)
file for details.

[s3_bucket_module]: https://docs.ansible.com/ansible/latest/modules/s3_bucket_module.html
[aws_s3_module]: https://docs.ansible.com/ansible/latest/modules/aws_s3_module.html
