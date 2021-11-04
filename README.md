[![Build Status](https://api.travis-ci.com/openclimatefix/pvoutput.svg)](https://travis-ci.com/openclimatefix/pvoutput/)

Download historical solar photovoltaic data from [PVOutput.org](https://pvoutput.org).

This code is a work-in-progress.  The aim is to provide both a Python library for interacting with [PVOutput.org's API](https://pvoutput.org/help.html#api), and a set of scripts for downloading lots of data :)

# Installation

## Register with PVOutput.org

You need to get an API key *and* a system ID from PVOutput.org.

If you don't have a PV system, click the "energy consumption only" box
when registering on PVOutput.  If you don't include a
system ID, then you'll get a "401 Unauthorized" response from the PVOutput API.

You can pass the API key and system ID into the `PVOutput` constructor.
Or, create a `~/.pvoutput.yml` file which looks like:

```yaml
api_key: <API key from PVOutput.org>
system_id: <SystemID from PVOutput.org>
```

### API quotas and paid subscriptions

* For free, PVOutput.org gives you 60 API requests per hour.  Per request, you can download one day of data for one PV system.  (See PVOutput's docs for more info about [rate limits](https://pvoutput.org/help/api_specification.html#rate-limits).)
* [Donating to PVOutput.org](https://pvoutput.org/help/donations.html#donations) increases your quota for a year to 300 requests per hour.
* To get more historical data, you can pay $600 Australian dollars for a year's 'Live System History' subscription for a single country ([more info here](https://pvoutput.org/help/data_services.html)).  This allows you to use the [`get batch status`](https://pvoutput.org/help/data_services.html#get-batch-status-service) API to download 900 PV-system-*years* per hour.  If you have subscribed to PVOutput's data service then add `data_service_url` to `~/.pvoutput.yml` or pass `data_service_url` to the `PVOutput` constructor.  The `data_service_url` should end in `.org`.  That is, don't include the `/service/r2` part of the URL.


## Install pvoutput Python library

`pip install -e git+https://github.com/openclimatefix/pvoutput#egg=pvoutput`


# Usage

See the [Quick Start notebook](examples/quick_start.ipynb).
