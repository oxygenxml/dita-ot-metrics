# DITA Metrics Report

Obtain different metrics from a DITA map.

The project can be used as a DITA OT plugin. Just copy the entire "dita-metrics-report" folder to the DITA OT "plugins" folder and run the integrator.

Or you can apply the XSLT processing directly.
Applying the XSLT stylesheets requires an XSLT 2.0 processor (Saxon 9) and the publishing is done in two stages:

  - The **report.xsl** XSLT stylesheet is applied on the main DITA Map. This produces a special XML document containing all the report data.
  * Then the **report2XHTML.xsl** XSLT stylesheet is applied on that XML output to produce the HTML output.
  
A short description of each reported metric can be found below:

  - Total number of maps and topics which are part of the project.
  - Total number of elements used in topics and maps along with a table presenting all element names and their usage counter.
  - The used elements used from each DITA domain.
  - Total number of attributes used in topics and maps along with a table presenting all attribute names and their usage counter.
  - Statistics about the conditional attributes used in the project.
  - Information about content reuse.
  * Text and content statistics, including both total words (word count) and unique words (vocabulary).
  - Tables containing list of largest and smallest topics and the number of words each one used.
  - Table containing a listing of all links to resources outside of the project.

## Importing the transformation scenario

The plugin repository includes a transformation scenario that you can import to your oXygen project file to make it easier to generate metrics reports.

1. Open your project’s root map in the **DITA Maps Manager** view.
2. From the menu, select **DITA Maps > Configure Transformation Scenario(s)**.
3. Click the ![settings](https://user-images.githubusercontent.com/129995/135727362-059f3c05-6218-47ed-9508-6136fcc6e1dd.png) **Settings** menu in the upper right corner of the **Configure Transformation Scenario(s)** dialog.
4. Select **Import Scenarios**.
5. Navigate to your local clone of the `dita-metrics-report` plugin repository.
6. Select the `DITA-Map-Metrics-Report.scenarios` file.

This adds a new _DITA Maps Metrics Report_ scenario to your project, with the following settings:

- The DITA-OT parameter `args.input` is set to `${cf}` _(current file)_.
- The `dita.dir` parameter is set to `${configured.ditaot.dir}` to use the DITA Open Toolkit installation specified in the oXygen [DITA Preferences](https://www.oxygenxml.com/doc/versions/23.1/ug-editor/topics/preferences-dita.html).
- The output directory is set to `${cfd}/out/metrics-report` to generate the report in the `/out/metrics-report/` subfolder of the current file directory.

# Visualizing the evolution of metrics between different versions of the documentation

You can try to generate metrics for multiple previous versions of your user's manual and then try to see how various indicators evolved. In order for this to work, you first need to use the "metrics-report-xml" transtype contributed by this plugin to create an XML report for each of the previous user guide versions that you are interested in comparing. You will need version control support to checkout the contents of your user's manual at a specific version.
As an example in the subfolder **evolution/samples** you can see four XML reports, obtained for four different versions of the Oxygen XML DITA documentation.

After you obtain those XML reports, you can create a transformation scenario in Oxygen and run the **evolution/generateDITATables.xsl**. The XSLT stylesheet will scan all XML reports and create a single DITA XML document containing tables showing how various indicators (like content reuse or number of words) have changed during releases. You can later publish that DITA topic to HTML or PDF outputs. If you have the SVG graphs generator (https://github.com/oxygenxml/dita-table-svg) plugin installed you will get diagrams showing the variation of various indicators. A sample generated report in HTML format can be found here: https://github.com/oxygenxml/dita-ot-metrics/blob/master/evolution/samples/generated.html

Copyright and License
---------------------
Copyright 2019 Syncro Soft SRL.

This project is licensed under Apache License 2.0, see the [LICENSE](LICENSE) file for details.

