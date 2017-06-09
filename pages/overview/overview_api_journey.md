---
title: API Journey
keywords: development,
tags: [engage,development,fhir]
sidebar: overview_sidebar
permalink: overview_api_journey.html
summary: Care Connect API journey outlines the approach of developing RESTful APIs and the journey taken to define and mature the Care Connect APIs
---

{% include important.html content="All phases outlined below are indicative and subject to on-going review." %}


# The Journey #

The API Journey is a guide from imagination and exploring to developing local APIs using Care Connect profiles all the way to deploying a live API.  

<?xml version="1.0" encoding="UTF-8"?>
<svg width="100%" viewBox="0 0 800 217" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
    <title>guide</title>
    <defs></defs>
    <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
        <g id="guide" transform="translate(0.000000, -13.000000)">
            <path d="M0,13.53 L105.555642,13.53 L132.098765,39.975123 L105.555642,66.42 L0,66.42 L26.5432716,39.975123 L0,13.53 Z" id="Fill-3" fill="#4F81BD"></path>
            <text id="Engage" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0104529625" fill="#FFFFFF">
                <tspan x="41.9667037" y="40.7087812">Engage</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="0.19908642" y="83.1018382">•</tspan>
            </text>
            <text id="Clinical-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0287456438" fill="#000000">
                <tspan x="11.3101975" y="83.1018382">Clinical	</tspan>
            </text>
            <text id="scenarios" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0295296162" fill="#000000">
                <tspan x="11.3101975" y="101.551838">scenarios</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="0.19908642" y="123.691838">•</tspan>
            </text>
            <text id="User-stories" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.000783972151" fill="#000000">
                <tspan x="11.3101975" y="123.691838">User stories</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="0.19908642" y="145.831838">•</tspan>
            </text>
            <text id="Use-cases" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.000783972151" fill="#000000">
                <tspan x="11.3101975" y="145.831838">Use cases</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="0.19908642" y="167.971838">•</tspan>
            </text>
            <text id="Benefits" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0238675959" fill="#000000">
                <tspan x="11.3101975" y="167.971838">Benefits</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="0.19908642" y="190.111875">•</tspan>
            </text>
            <text id="Clinical-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0287456438" fill="#000000">
                <tspan x="11.3101975" y="190.111875">Clinical	</tspan>
            </text>
            <text id="inspiration" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0128048779" fill="#000000">
                <tspan x="11.3101975" y="208.561875">inspiration</tspan>
            </text>
            <path d="M111.111111,13.53 L216.66679,13.53 L243.209877,39.975123 L216.66679,66.42 L111.111111,66.42 L137.654321,39.975123 L111.111111,13.53 Z" id="Fill-5" fill="#4F81BD"></path>
            <text id="Explore" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0104529625" fill="#FFFFFF">
                <tspan x="153.195926" y="40.7087812">Explore</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="111.428309" y="83.1018382">•</tspan>
            </text>
            <text id="Impl" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0293554012" fill="#000000">
                <tspan x="122.539383" y="83.1018382">Impl</tspan>
            </text>
            <text id="Guide" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.010365854" fill="#000000">
                <tspan x="157.107284" y="83.1018382">Guide</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="111.428309" y="105.241838">•</tspan>
            </text>
            <text id="Resource-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0247386768" fill="#000000">
                <tspan x="122.539383" y="105.241838">Resource	</tspan>
            </text>
            <text id="Profiles" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0148083633" fill="#000000">
                <tspan x="122.539383" y="123.691838">Profiles</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="111.428309" y="145.831838">•</tspan>
            </text>
            <text id="API" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0066202092" fill="#000000">
                <tspan x="122.539383" y="145.831838">API</tspan>
            </text>
            <text id="definitions" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.021777004" fill="#000000">
                <tspan x="122.539383" y="164.281838">definitions</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="111.428309" y="186.421875">•</tspan>
            </text>
            <text id="Search-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0264808368" fill="#000000">
                <tspan x="122.539383" y="186.421875">Search	</tspan>
            </text>
            <text id="parameters" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.021777004" fill="#000000">
                <tspan x="122.539383" y="206.101875">parameters</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="111.428309" y="228.241875">•</tspan>
            </text>
            <text id="Value-sets" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0583623685" fill="#000000">
                <tspan x="122.539383" y="228.241875">Value sets</tspan>
            </text>
            <path d="M222.222222,13.53 L327.777901,13.53 L354.320988,39.975123 L327.777901,66.42 L222.222222,66.42 L248.765432,39.975123 L222.222222,13.53 Z" id="Fill-7" fill="#4F81BD"></path>
            <text id="Design-&amp;-Build-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0243031345" fill="#FFFFFF">
                <tspan x="266.231831" y="33">Design &amp; </tspan>
                <tspan x="268.336543" y="50.4199982">Build	</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="222.657531" y="83.1018382">•</tspan>
            </text>
            <text id="Producer-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0148083633" fill="#000000">
                <tspan x="233.768642" y="83.1018382">Producer	</tspan>
            </text>
            <text id="APIs" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0066202092" fill="#000000">
                <tspan x="233.768642" y="101.551838">APIs</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="222.657531" y="123.691838">•</tspan>
            </text>
            <text id="Code-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0287456438" fill="#000000">
                <tspan x="233.768642" y="123.691838">Code	</tspan>
            </text>
            <text id="examples" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.00174216041" fill="#000000">
                <tspan x="233.768642" y="142.141838">examples</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="222.657531" y="164.281838">•</tspan>
            </text>
            <text id="Validation-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0583623685" fill="#000000">
                <tspan x="233.768642" y="164.281838">Validation	</tspan>
            </text>
            <text id="tools" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0192508716" fill="#000000">
                <tspan x="233.768642" y="183.961875">tools</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="222.657531" y="206.101875">•</tspan>
            </text>
            <text id="Security-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0264808368" fill="#000000">
                <tspan x="233.768642" y="206.101875">Security	</tspan>
            </text>
            <text id="examples" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.00174216041" fill="#000000">
                <tspan x="233.768642" y="224.551875">examples</tspan>
            </text>
            <path d="M333.333333,13.53 L440.123457,13.53 L466.666667,39.975 L440.123457,66.42 L333.333333,66.42 L359.876543,39.975 L333.333333,13.53 Z" id="Fill-9" fill="#4F81BD"></path>
            <text id="Test" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0508710817" fill="#FFFFFF">
                <tspan x="386.768395" y="40.7087812">Test</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="333.886667" y="83.1018382">•</tspan>
            </text>
            <text id="Test-data" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0508710817" fill="#000000">
                <tspan x="344.997778" y="83.1018382">Test	data</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="333.886667" y="105.241838">•</tspan>
            </text>
            <text id="Security-tests" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0264808368" fill="#000000">
                <tspan x="344.997778" y="105.241838">Security tests</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="333.886667" y="127.381838">•</tspan>
            </text>
            <text id="Reference-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0247386768" fill="#000000">
                <tspan x="344.997778" y="127.381838">Reference	</tspan>
            </text>
            <text id="servers" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0295296162" fill="#000000">
                <tspan x="344.997778" y="145.831838">servers</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="333.886667" y="167.971838">•</tspan>
            </text>
            <text id="Secure-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0264808368" fill="#000000">
                <tspan x="344.997778" y="167.971838">Secure	</tspan>
            </text>
            <text id="store" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0295296162" fill="#000000">
                <tspan x="396.84963" y="167.971838">store</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="333.886667" y="190.111875">•</tspan>
            </text>
            <text id="Example-data" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0104529625" fill="#000000">
                <tspan x="344.997778" y="190.111875">Example data</tspan>
            </text>
            <path d="M445.679012,13.53 L551.234691,13.53 L577.777778,39.975123 L551.234691,66.42 L445.679012,66.42 L472.222346,39.975123 L445.679012,13.53 Z" id="Fill-11" fill="#4F81BD"></path>
            <text id="Accredit" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0066202092" fill="#FFFFFF">
                <tspan x="483.18284" y="40.7087812">Accredit</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="445.115926" y="83.1018382">•</tspan>
            </text>
            <text id="Automated-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0066202092" fill="#000000">
                <tspan x="456.227037" y="83.1018382">Automated	</tspan>
            </text>
            <text id="tests" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0192508716" fill="#000000">
                <tspan x="456.227037" y="101.551838">tests</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="445.115926" y="123.691838">•</tspan>
            </text>
            <text id="Test--Reports" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0508710817" fill="#000000">
                <tspan x="456.227037" y="123.691838">Test	 Reports</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="445.115926" y="145.831838">•</tspan>
            </text>
            <text id="Test--Evidence" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0508710817" fill="#000000">
                <tspan x="456.227037" y="145.831838">Test	 Evidence</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="445.115926" y="167.971838">•</tspan>
            </text>
            <text id="Conformance-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0287456438" fill="#000000">
                <tspan x="456.227037" y="167.971838">Conformance	</tspan>
            </text>
            <text id="reports" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.00705574965" fill="#000000">
                <tspan x="456.227037" y="186.421875">reports</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="445.115926" y="208.561875">•</tspan>
            </text>
            <text id="Accreditation-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0066202092" fill="#000000">
                <tspan x="456.227037" y="208.561875">Accreditation	</tspan>
            </text>
            <text id="checklist" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.00487804832" fill="#000000">
                <tspan x="456.227037" y="228.241875">checklist</tspan>
            </text>
            <path d="M556.790123,13.53 L662.345802,13.53 L688.888889,39.975123 L662.345802,66.42 L556.790123,66.42 L583.333457,39.975123 L556.790123,13.53 Z" id="Fill-13" fill="#4F81BD"></path>
            <text id="Deploy-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0243031345" fill="#FFFFFF">
                <tspan x="599.34716" y="31.2500812">Deploy	</tspan>
            </text>
            <text id="(Pilot)" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0150696868" fill="#FFFFFF">
                <tspan x="603.050864" y="49.7000812">(Pilot)</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="556.344938" y="83.1018382">•</tspan>
            </text>
            <text id="API-harness" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0066202092" fill="#000000">
                <tspan x="567.456049" y="83.1018382">API harness</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="556.344938" y="105.241838">•</tspan>
            </text>
            <text id="Warranted-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0286585391" fill="#000000">
                <tspan x="567.456049" y="105.241838">Warranted	</tspan>
            </text>
            <text id="environment" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.00174216041" fill="#000000">
                <tspan x="567.456049" y="123.691838">environment</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="556.344938" y="145.831838">•</tspan>
            </text>
            <text id="IG-/-IS" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0293554012" fill="#000000">
                <tspan x="567.456049" y="145.831838">IG / IS</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="556.344938" y="167.971838">•</tspan>
            </text>
            <text id="Spine-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0264808368" fill="#000000">
                <tspan x="567.456049" y="167.971838">Spine	</tspan>
            </text>
            <text id="comms" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.00487804832" fill="#000000">
                <tspan x="609.431358" y="167.971838">comms</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="556.344938" y="190.111875">•</tspan>
            </text>
            <text id="Record" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0247386768" fill="#000000">
                <tspan x="567.456049" y="190.111875">Record</tspan>
            </text>
            <text id="locator" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0128048779" fill="#000000">
                <tspan x="567.456049" y="208.561875">locator</tspan>
            </text>
            <path d="M667.901235,13.53 L773.456914,13.53 L800,39.975123 L773.456914,66.42 L667.901235,66.42 L694.444568,39.975123 L667.901235,13.53 Z" id="Fill-15" fill="#4F81BD"></path>
            <text id="Deploy-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0243031345" fill="#FFFFFF">
                <tspan x="710.57642" y="31.2500812">Deploy	</tspan>
            </text>
            <text id="(Live)" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0150696868" fill="#FFFFFF">
                <tspan x="716.749259" y="49.7000812">(Live)</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="667.574198" y="83.1018382">•</tspan>
            </text>
            <text id="Registry" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0247386768" fill="#000000">
                <tspan x="678.685309" y="83.1018382">Registry</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="667.574198" y="105.241838">•</tspan>
            </text>
            <text id="Monitor" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.00182926829" fill="#000000">
                <tspan x="678.685309" y="105.241838">Monitor</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="667.574198" y="127.381838">•</tspan>
            </text>
            <text id="Support" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0264808368" fill="#000000">
                <tspan x="678.685309" y="127.381838">Support</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="667.574198" y="148.291838">•</tspan>
            </text>
            <text id="Conformance-" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0287456438" fill="#000000">
                <tspan x="678.685309" y="148.291838">Conformance	</tspan>
            </text>
            <text id="statement" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="-0.0295296162" fill="#000000">
                <tspan x="678.685309" y="167.971838">statement</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" fill="#000000">
                <tspan x="667.574198" y="190.111875">•</tspan>
            </text>
            <text id="Extensions" font-family="HelveticaNeue, Helvetica Neue" font-size="15" font-weight="normal" letter-spacing="0.0104529625" fill="#000000">
                <tspan x="678.685309" y="190.111875">Extensions</tspan>
            </text>
            <rect id="l-engage" fill-opacity="0" fill="#FFFFFF" x="0" y="0" width="108.641975" height="239.85">
                <a xlink:href="/engage.html" target="_top">
                    <text x="10" y="20" width="100%" height="100%" style="text-anchor: middle">test</text>
                </a>
            </rect>
            <rect id="l-explore" fill-opacity="0" fill="#FFFFFF" x="113.580247" y="0" width="108.641975" height="239.85">
                <a xlink:href="https://nhsconnect.github.io/CareConnectAPI/restfulapis.html" target="_top">
                    <text x="10" y="20" width="100%" height="100%" style="text-anchor: middle"> </text>
                </a>
            </rect>
            <rect id="l-design" fill-opacity="0" fill="#FFFFFF" x="223" y="0" width="108.641975" height="239.85"></rect>
            <rect id="l-test" fill-opacity="0" fill="#FFFFFF" x="332.098765" y="0" width="108.641975" height="239.85"></rect>
            <rect id="l-accredit" fill-opacity="0" fill="#FFFFFF" x="445.679012" y="0" width="108.641975" height="239.85"></rect>
            <rect id="l-deploy" fill-opacity="0" fill="#FFFFFF" x="556.344938" y="0" width="108.641975" height="239.85"></rect>
            <rect id="l-live" fill-opacity="0" fill="#FFFFFF" x="669.135802" y="0" width="132.098765" height="239.85"></rect>
        </g>
    </g>
</svg>


The above steps outline a complete API journey .

# Profile journey #

The current site focuses on a typical API Developer's Journey as highlighted by the green boxes below in the developer journey:

<img src="images/roadmap/profile-focus.jpg" style="width:100%;max-width: 100%;">

NHS Digital is contributing to progressing the profile developmenet, the testing process and invitations are open for the INTEROPen community to get involved and progress the wider developer ecosystem. Please see the explanation of the complete development roadmap below.

{% include custom/contribute.html content="Please contact [careconnect@interopen.org] to get involved." %}

# How this fits into the wider journey? #

The current site focuses on a typical API Developer's Journey as highlighted by the green boxes below in the developer journey:

<img src="images/roadmap/guide-focus.jpg" style="width:100%;max-width: 100%;">

NHS Digital is contributing to progressing the profile developmenet, the testing process and invitations are open for the INTEROPen community to get involved and progress the wider developer ecosystem.

Please see the explanation of the complete development roadmap.
