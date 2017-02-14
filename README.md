# DITA Metrics Report

Obtain different metrics from a DITA map.

Applying the XSLT stylesheets requires an XSLT 2.0 processor (Saxon 9).

First the **report/report.xsl** XSLT stylesheet should be applied on the DITA Map. This produces a special XML document containing all the report data.
After this, on the XML document produced on stage 1  you should apply the **report/report2XHTML.xsl** XSLT stylesheet which produces the HTML output.


## License

This project is licensed under MPL 2.0, see the [LICENSE](LICENSE) file for details.

