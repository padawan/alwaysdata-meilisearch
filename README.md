# alwaysdata-meilisearch
Alwaysdata Marketplace installation script for [self-hosted Meilisearch](https://www.meilisearch.com/docs/learn/self_hosted/getting_started_with_self_hosted_meilisearch).

You will need an alwaysdata account to use it. If you don't have one, please do me a favor and use [this referal link](https://www.alwaysdata.com/en/register/?from=246ec3b6) to register.

Please note that, at this time, the size of the Meilisearch binary alone does not allow for its installation on a free plan.

## Installation

1. Go to your Sites admin page at https://admin.alwaysdata.com/site/
2. Click on **+ Install an application**
3. Click on **Meilisearch** in the marketplace applications listing
4. In the Site form, fill out the **Addresses** and **Installation directory** fields, and check the **Accept the conditions** checkbox
5. Click **Submit**

After the installation, you should have a new site with Meilisearch configured as a user program, and you should find the following directories and files in your installation directory:

```
api_keys.json
.config
config.toml
data.ms
dumps
meilisearch
```

Go to the site and check that it displays the Meilisearch Mini Dashboard.

## Further configuration

Meilisearch is lauched using the following command: `./meilisearch --config-file-path="./config.toml"` and can be further configured by editing the `config.toml` file. Check the [Meilisearch self-hosted configuration file](https://www.meilisearch.com/docs/learn/self_hosted/configure_meilisearch_at_launch#configuration-file) documentation for all the available options.

N.B.: do NOT change the `http_addr` line (the IP and PORT are preconfigured with the correct values for your site).

## Security

This script automatically generates a random master key to secure the instance. This key is visible in `config.toml` around these lines:

```
# Sets the instance's master key, automatically protecting all routes except GET /health.
# https://www.meilisearch.com/docs/learn/configuration/instance_options#master-key
master_key = "875bb119-a278-4940-8a05-5d8755994a74"
```

You should NOT use this master key as an API key.

As a convenience, the script automatically outputs the two corresponding default API keys ("Default Search API Key" and "Default Admin API Key") in `api_keys.json`.

You can change the `master_key` value afterwards. If you do so, you will need to fetch the new default keys using the Meilisearch API.

See [Securing your project](https://www.meilisearch.com/docs/learn/security/basic_security) for more information on the master and API keys.

## Misc.

- [**meili**search GitHub repository](https://github.com/meilisearch)
- [self-hosted Meilisearch documentation](https://www.meilisearch.com/docs/learn/self_hosted/getting_started_with_self_hosted_meilisearch)
- [alwaysdata Marketplace help](https://help.alwaysdata.com/en/marketplace/)