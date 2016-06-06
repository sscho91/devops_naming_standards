# Global Naming Group Syntax


```
<splunk_sourcetype> ::= <tower> "_" <env_name>"_"[<cluster_name> "_"] <zone> "_" <application> "_" <component> "_" <artifact>

<splunk_classname> ::= <tower> "_" <env_name> "_" [<cluster_name> "_"] <zone> "_" <application> "_" <component>

<newrelic_group_names> ::= <tower> "_" <env_name> "_" [<cluster_name> "_"]<zone> "_" <application> "_" <component>
```

# Syntax Components

```
<tower> ::= "ee" | "fm" | "pm" | "shop" | "mcr"

<env_name> ::= "dev" <env_identifier> |
               "test"  <env_identifier> |
               "impl" <env_impl_identifier> [ "-" <aws_region_identifier> ] |
               "prod" [ "-" ( <env_prod_identifier> | <aws_region_identifier> ) ]

<aws_region_identifier> ::= "east" | "west"

<env_identifier> ::= [0-9] | "s"

<env_impl_identifier> ::= "0" | "1a" | "1b" | "2"

<env_prod_identifier> ::= "dr" | "q"

<cluster_name> ::= "rollup" |
                   "steelblue" |
				   "white" |
                   "batch1" |
				   <other>

<zone> ::= "dmz" | "pz" | "az" | "dz"

<application> ::= "app" | "online" | "batch" | "ses-online"

<occbatch_type> ::= "all" | "moen" | "buu" | "irsreporting"

<component_classifier> ::= "en" | "es" | "ui" | "svcs" | "db"

<component> ::= "app" |
		   	 "batch" |
		   	 "oocbatch" [ "-" <occbatch_type> ] |
		   	 "rp" [ "-" <component_classifier> ] |
		   	 “lb” [ "-" <component_classifier> ] |
		   	 "agigw" [ "-" <component_classifier> ] |
		   	 "cms" [ "-" <component_classifier> ] |
			    "db” ["-" <component_classifier> ] |
			    "cache" [ "-" ("primary" | "secondary" | "batch") ]

<artifact> ::= "server-log" | [ [1-9][0-9]{3,4} "-"] "access-log" |   "error-log" |
"job-log" | "stdout-log" | "stderr-log" | "oracle-log" | "haproxy-log"
 ```
#E&E Examples
```
ee_prod_pz_online_rp-en_access-log
ee_prod_pz_online_rp-en_error-log
ee_prod_pz_online_rp-en_server-log
ee_prod_pz_online_rp-es_access-log
ee_prod_pz_online_rp-es_error-log
ee_prod_pz_online_rp-es_server-log
ee_prod_pz_online_apigw_server-log
ee_prod_pz_online_apigw-ccr_server-log
ee_prod_pz_online_cache-apigw_server-log
ee_prod_pz_online_db-apigw_server-log
ee_prod_az_online_apigw-esdcu_server-log
ee_prod_az_online_lb_access-log
ee_prod_az_online_lb_error-log
ee_prod_rollup_az_online_app_server-log
ee_prod_steelblue_az_online_app_server-log
ee_prod_white_az_online_server-log
ee_prod_az_online_cache-primary_server-log
ee_prod_az_online_cache-secondary_server-log
ee_prod_dz_batch_batch-batch1_server-log
ee_prod_dz_batch_oocbatch_stdout-log
ee_prod_dz_batch_oocbatch_stderr-log
ee_prod_dz_batch_cache_server-log
ee_prod_dz_batch_db_oracle-log
ee_prod_dz_online_cms_server-log
ee_prod_dz_online_cms-db_server-log
ee_prod_online_db_7999-access-log
ee_prod_online_db_2223-access-log

```
#MCR Examples
```
mcr_prod-east_pz_app_rp-ui_access-log "\n"
mcr_prod-east_pz_app_rp-ui_server-log"\n"
mcr_prod-east_pz_app_rp-ui_error-log"\n"
mcr_prod-east_pz_app_rp-svcs_access-log"\n"
mcr_prod-east_pz_app_rp-svcs_error-log"\n"
mcr_prod-east_pz_app_rp-svcs_server-log"\n"
mcr_prod-east_az_app_lb-app_server-log"\n"
mcr_prod-east_az_app_app_server-log"\n"
mcr_prod-east_az_app_agigw-lb_server-log"\n"
mcr_prod-east_az_app_agigw_server-log"\n"
mcr_prod-east_dz_app_batch_server-log"\n"
mcr_prod-east_dz_app_lb-db_server-log"\n"
mcr_prod-east_dz_app_db_server-log
```
