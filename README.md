# EC2 and Lightsail Price Tracker

This project automatically fetches and updates pricing information for Amazon EC2 instances and Amazon Lightsail bundles across all regions. It uses GitHub Actions to run daily updates and store the results in this repository.

## Features

- Daily updates of EC2 on-demand instance prices for all regions
- Daily updates of Lightsail bundle prices (same across all regions)
- Supports both Linux and Windows EC2 instances
- Caching mechanism to reduce unnecessary API calls
- Manual trigger option with force update capability

## How It Works

The project uses a GitHub Actions workflow to:

1. Fetch EC2 pricing data for all regions and both Linux and Windows operating systems
2. Fetch Lightsail bundle pricing data
3. Store the data in structured directories within the repository
4. Commit and push the changes daily

The workflow utilizes functions from the [easy-aws-helper](https://github.com/rioastamal/easy-aws-helper) project to interact with AWS services and retrieve pricing information.

## Directory Structure

- `ec2/on-demand/<os>/<region>/prices.txt`: EC2 instance prices for each OS and region
- `ec2/on-demand/<os>/<region>/cache.txt`: Cache file for EC2 prices
- `lightsail/prices.txt`: Lightsail bundle prices
- `lightsail/cache.txt`: Cache file for Lightsail prices

## Sample Output

Here's an example of the EC2 pricing output for Linux instances in the ap-southeast-1 region (`ec2/on-demand/linux/ap-southeast-1/prices.txt`):

```
+---------------------+------+------------+----------+-----------+--------------+---------------+--------------+
| Instance type       | vCPU | CPU type   | RAM (GB) | Disk (GB) | Price ($/hr) | Price ($/day) | Price ($/mo) |
+---------------------+------+------------+----------+-----------+--------------+---------------+--------------+
| t2.nano             | 1    | i386       | 0.5      | None      |  0.0073      | 0.18          | 5.33         |
| t3.nano             | 2    | x86_64     | 0.5      | None      |  0.0066      | 0.16          | 4.82         |
| t3a.nano            | 2    | x86_64     | 0.5      | None      |  0.0059      | 0.14          | 4.31         |
| t4g.nano            | 2    | arm64      | 0.5      | None      |  0.0053      | 0.13          | 3.87         |
| t1.micro            | 1    | i386       | 0.6      | None      |  0.02        | 0.48          | 14.61        |
| t2.micro            | 1    | i386       | 1.0      | None      |  0.0146      | 0.35          | 10.67        |
| t3.micro            | 2    | x86_64     | 1.0      | None      |  0.0132      | 0.32          | 9.64         |
| t3a.micro           | 2    | x86_64     | 1.0      | None      |  0.0118      | 0.28          | 8.62         |
| t4g.micro           | 2    | arm64      | 1.0      | None      |  0.0106      | 0.25          | 7.74         |
...
```

## Usage

The price updates are automated, but you can also manually trigger the workflow:

1. Go to the "Actions" tab in the GitHub repository
2. Select the "Update EC2 and Lightsail Instance Prices" workflow
3. Click "Run workflow"
4. Choose whether to force update EC2 and/or Lightsail prices ignoring the cache

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open-source and available under the [MIT License](LICENSE).

## Acknowledgements

This project makes use of the [easy-aws-helper](https://github.com/rioastamal/easy-aws-helper) to generate the prices data.
