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
<svg width="648px" height="200px" viewBox="0 0 648 200" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
    <title>Impl guide - links</title>
    <defs></defs>
    <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
        <g id="guide">
            <rect id="l-engage" fill="#FFFFFF" x="0" y="5" width="88" height="195">
                <a xlink:href="/engage.html" target="_top">
                    <text x="100%" y="100%" style="text-anchor: middle"> </text>
                </a>
            </rect>
            <rect id="l-explore" fill="#FFFFFF" x="92" y="0" width="88" height="195"></rect>
            <rect id="l-design" fill="#FFFFFF" x="185.3526" y="0" width="88" height="195"></rect>
            <rect id="l-test" fill="#FFFFFF" x="269" y="0" width="88" height="195"></rect>
            <rect id="l-accredit" fill="#FFFFFF" x="361" y="0" width="88" height="195"></rect>
            <rect id="l-deploy" fill="#FFFFFF" x="450.6394" y="0" width="88" height="195"></rect>
            <rect id="l-live" fill="#FFFFFF" x="542" y="0" width="88" height="195"></rect>
            <path d="M0,11 L85.50007,11 L107,32.5001 L85.50007,54 L0,54 L21.50005,32.5001 L0,11 Z" id="Fill-3" fill="#4F81BD"></path>
            <text id="Engage" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0102857146" fill="#FFFFFF">
                <tspan x="33.99303" y="32.7144562">Engage</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="0.16126" y="67.1803562">•</tspan>
            </text>
            <text id="Clinical-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0282857139" fill="#000000">
                <tspan x="9.16126" y="67.1803562">Clinical	</tspan>
            </text>
            <text id="scenarios" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0290571433" fill="#000000">
                <tspan x="9.16126" y="82.1803562">scenarios</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="0.16126" y="100.180356">•</tspan>
            </text>
            <text id="User-stories" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.000771428575" fill="#000000">
                <tspan x="9.16126" y="100.180356">User	stories</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="0.16126" y="118.180356">•</tspan>
            </text>
            <text id="Use-cases" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.000771428575" fill="#000000">
                <tspan x="9.16126" y="118.180356">Use cases</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="0.16126" y="136.180356">•</tspan>
            </text>
            <text id="Benefits" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0234857146" fill="#000000">
                <tspan x="9.16126" y="136.180356">Benefits</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="0.16126" y="154.180386">•</tspan>
            </text>
            <text id="Clinical-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0282857139" fill="#000000">
                <tspan x="9.16126" y="154.180386">Clinical	</tspan>
            </text>
            <text id="inspiration" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0126" fill="#000000">
                <tspan x="9.16126" y="169.180386">inspiration</tspan>
            </text>
            <path d="M90,11 L175.5001,11 L197,32.5001 L175.5001,54 L90,54 L111.5,32.5001 L90,11 Z" id="Fill-5" fill="#4F81BD"></path>
            <text id="Explore" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0102857146" fill="#FFFFFF">
                <tspan x="124.0887" y="32.7144562">Explore</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="90.25693" y="67.1803562">•</tspan>
            </text>
            <text id="Impl" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0288857147" fill="#000000">
                <tspan x="99.2569" y="67.1803562">Impl</tspan>
            </text>
            <text id="Guide" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0102000004" fill="#000000">
                <tspan x="127.2569" y="67.1803562">Guide</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="90.25693" y="85.1803562">•</tspan>
            </text>
            <text id="Resource-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0243428573" fill="#000000">
                <tspan x="99.2569" y="85.1803562">Resource	</tspan>
            </text>
            <text id="Profiles" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0145714292" fill="#000000">
                <tspan x="99.2569" y="100.180356">Profiles</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="90.25693" y="118.180356">•</tspan>
            </text>
            <text id="API" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.00651428569" fill="#000000">
                <tspan x="99.2569" y="118.180356">API</tspan>
            </text>
            <text id="definitions" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.021428572" fill="#000000">
                <tspan x="99.2569" y="133.180356">definitions</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="90.25693" y="151.180386">•</tspan>
            </text>
            <text id="Search-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0260571428" fill="#000000">
                <tspan x="99.2569" y="151.180386">Search	</tspan>
            </text>
            <text id="parameters" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.021428572" fill="#000000">
                <tspan x="99.2569" y="167.180386">parameters</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="90.25693" y="185.180386">•</tspan>
            </text>
            <text id="Value-sets" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0574285723" fill="#000000">
                <tspan x="99.2569" y="185.180386">Value sets</tspan>
            </text>
            <path d="M180,11 L265.5001,11 L287,32.5001 L265.5001,54 L180,54 L201.5,32.5001 L180,11 Z" id="Fill-7" fill="#4F81BD"></path>
            <text id="Design-&amp;-Build-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.023914285" fill="#FFFFFF">
                <tspan x="209.1843" y="25.0244562">Design	</tspan>
                <tspan x="209.1843" y="39.3604548">&amp; Build	</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="180.3526" y="67.1803562">•</tspan>
            </text>
            <text id="Producer-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0145714292" fill="#000000">
                <tspan x="189.3526" y="67.1803562">Producer	</tspan>
            </text>
            <text id="APIs" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.00651428569" fill="#000000">
                <tspan x="189.3526" y="82.1803562">APIs</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="180.3526" y="100.180356">•</tspan>
            </text>
            <text id="Code-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0282857139" fill="#000000">
                <tspan x="189.3526" y="100.180356">Code	</tspan>
            </text>
            <text id="examples" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.00171428581" fill="#000000">
                <tspan x="189.3526" y="115.180356">examples</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="180.3526" y="133.180356">•</tspan>
            </text>
            <text id="Validation-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0574285723" fill="#000000">
                <tspan x="189.3526" y="133.180356">Validation	</tspan>
            </text>
            <text id="tools" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0189428572" fill="#000000">
                <tspan x="189.3526" y="149.180386">tools</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="180.3526" y="167.180386">•</tspan>
            </text>
            <text id="Security-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0260571428" fill="#000000">
                <tspan x="189.3526" y="167.180386">Security	</tspan>
            </text>
            <text id="examples" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.00171428581" fill="#000000">
                <tspan x="189.3526" y="182.180386">examples</tspan>
            </text>
            <path d="M270,11 L356.5,11 L378,32.5 L356.5,54 L270,54 L291.5,32.5 L270,11 Z" id="Fill-9" fill="#4F81BD"></path>
            <text id="Test" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.050057143" fill="#FFFFFF">
                <tspan x="313.2824" y="32.7144562">Test</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="270.4482" y="67.1803562">•</tspan>
            </text>
            <text id="Test-data" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.050057143" fill="#000000">
                <tspan x="279.4482" y="67.1803562">Test	data</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="270.4482" y="85.1803562">•</tspan>
            </text>
            <text id="Security-tests" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0260571428" fill="#000000">
                <tspan x="279.4482" y="85.1803562">Security tests</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="270.4482" y="103.180356">•</tspan>
            </text>
            <text id="Reference-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0243428573" fill="#000000">
                <tspan x="279.4482" y="103.180356">Reference	</tspan>
            </text>
            <text id="servers" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0290571433" fill="#000000">
                <tspan x="279.4482" y="118.180356">servers</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="270.4482" y="136.180356">•</tspan>
            </text>
            <text id="Secure-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0260571428" fill="#000000">
                <tspan x="279.4482" y="136.180356">Secure	</tspan>
            </text>
            <text id="store" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0290571433" fill="#000000">
                <tspan x="321.4482" y="136.180356">store</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="270.4482" y="154.180386">•</tspan>
            </text>
            <text id="Example-data" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0102857146" fill="#000000">
                <tspan x="279.4482" y="154.180386">Example data</tspan>
            </text>
            <path d="M361,11 L446.5001,11 L468,32.5001 L446.5001,54 L361,54 L382.5001,32.5001 L361,11 Z" id="Fill-11" fill="#4F81BD"></path>
            <text id="Accredit" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.00651428569" fill="#FFFFFF">
                <tspan x="391.3781" y="32.7144562">Accredit</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="360.5439" y="67.1803562">•</tspan>
            </text>
            <text id="Automated-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.00651428569" fill="#000000">
                <tspan x="369.5439" y="67.1803562">Automated	</tspan>
            </text>
            <text id="tests" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0189428572" fill="#000000">
                <tspan x="369.5439" y="82.1803562">tests</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="360.5439" y="100.180356">•</tspan>
            </text>
            <text id="Test-reports" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.050057143" fill="#000000">
                <tspan x="369.5439" y="100.180356">Test	reports</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="360.5439" y="118.180356">•</tspan>
            </text>
            <text id="Test-Evidence" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.050057143" fill="#000000">
                <tspan x="369.5439" y="118.180356">Test	Evidence</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="360.5439" y="136.180356">•</tspan>
            </text>
            <text id="Conformance-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0282857139" fill="#000000">
                <tspan x="369.5439" y="136.180356">Conformance	</tspan>
            </text>
            <text id="reports" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.00694285752" fill="#000000">
                <tspan x="369.5439" y="151.180386">reports</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="360.5439" y="169.180386">•</tspan>
            </text>
            <text id="Accreditation-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.00651428569" fill="#000000">
                <tspan x="369.5439" y="169.180386">Accreditation	</tspan>
            </text>
            <text id="checklist" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.00479999976" fill="#000000">
                <tspan x="369.5439" y="185.180386">checklist</tspan>
            </text>
            <path d="M451,11 L536.5001,11 L558,32.5001 L536.5001,54 L451,54 L472.5001,32.5001 L451,11 Z" id="Fill-13" fill="#4F81BD"></path>
            <text id="Deploy-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.023914285" fill="#FFFFFF">
                <tspan x="485.4712" y="25.0244562">Deploy	</tspan>
            </text>
            <text id="(Pilot)" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.014828572" fill="#FFFFFF">
                <tspan x="488.4712" y="40.0244562">(Pilot)</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="450.6394" y="67.1803562">•</tspan>
            </text>
            <text id="API-harness" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.00651428569" fill="#000000">
                <tspan x="459.6394" y="67.1803562">API harness</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="450.6394" y="85.1803562">•</tspan>
            </text>
            <text id="Warranted-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0282000024" fill="#000000">
                <tspan x="459.6394" y="85.1803562">Warranted	</tspan>
            </text>
            <text id="environment" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.00171428581" fill="#000000">
                <tspan x="459.6394" y="100.180356">environment</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="450.6394" y="118.180356">•</tspan>
            </text>
            <text id="IG-/-IS" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0288857147" fill="#000000">
                <tspan x="459.6394" y="118.180356">IG / IS</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="450.6394" y="136.180356">•</tspan>
            </text>
            <text id="Spine-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0260571428" fill="#000000">
                <tspan x="459.6394" y="136.180356">Spine	</tspan>
            </text>
            <text id="comms" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.00479999976" fill="#000000">
                <tspan x="493.6394" y="136.180356">comms</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="450.6394" y="154.180386">•</tspan>
            </text>
            <text id="Record" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0243428573" fill="#000000">
                <tspan x="459.6394" y="154.180386">Record</tspan>
            </text>
            <text id="locator" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0126" fill="#000000">
                <tspan x="459.6394" y="169.180386">locator</tspan>
            </text>
            <path d="M541,11 L626.5001,11 L648,32.5001 L626.5001,54 L541,54 L562.5001,32.5001 L541,11 Z" id="Fill-15" fill="#4F81BD"></path>
            <text id="Deploy-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.023914285" fill="#FFFFFF">
                <tspan x="575.5669" y="25.0244562">Deploy	</tspan>
            </text>
            <text id="(Live)" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.014828572" fill="#FFFFFF">
                <tspan x="580.5669" y="40.0244562">(Live)</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="540.7351" y="67.1803562">•</tspan>
            </text>
            <text id="Registry" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0243428573" fill="#000000">
                <tspan x="549.7351" y="67.1803562">Registry</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="540.7351" y="85.1803562">•</tspan>
            </text>
            <text id="Monitor" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.00179999997" fill="#000000">
                <tspan x="549.7351" y="85.1803562">Monitor</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="540.7351" y="103.180356">•</tspan>
            </text>
            <text id="Support" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0260571428" fill="#000000">
                <tspan x="549.7351" y="103.180356">Support</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="540.7351" y="120.180356">•</tspan>
            </text>
            <text id="Conformance-" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0282857139" fill="#000000">
                <tspan x="549.7351" y="120.180356">Conformance	</tspan>
            </text>
            <text id="statement" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="-0.0290571433" fill="#000000">
                <tspan x="549.7351" y="136.180356">statement</tspan>
            </text>
            <text id="•" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" fill="#000000">
                <tspan x="540.7351" y="154.180386">•</tspan>
            </text>
            <text id="Extensions" font-family="HelveticaNeue, Helvetica Neue" font-size="12" font-weight="normal" letter-spacing="0.0102857146" fill="#000000">
                <tspan x="549.7351" y="154.180386">Extensions</tspan>
            </text>
        </g>
    </g>
</svg>

<img src="images/roadmap/guide.jpg" style="width:100%;max-width: 100%;">

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
