# Integration using Emailed Login

<PageHeader />

MV Dashboard can be used as a vehicle for presenting reports generated by the host MultiValue server. An example where this might be used is to have nightly reporting processes save the images of reports as they are run and to email a link for each report that the recipient can click on to view the report.

The request for this capability came about because of periodic issues when attempting to include html columnar reports in the body of an email. Letting MV Dashboard present the report through the browser eliminates that issue.

The report images can be either plain text or html. They should be stored in the MVDB.EMAILED.HTML file in the MVDB account. The first 5 characters of the record id in this file should be the 5 digit internal date when the report was generated. All reports in this file for more than 10 days will be automatically deleted.

If a monthly sales report was saved in the MVDB.EMAILED.HTML file as 17503\_MOSALES, the URL string to view that report through the dashboard would be:

```
http://ipaddress:8180/dbc/MVDB.MAIN?loginid=emailed&htmlid=17503_MOSALES 
```




> NOTE: You must enable the emailed login from the Administrative Configuration widget in the Administrator dashboard before this feature can be used.

<PageFooter />
