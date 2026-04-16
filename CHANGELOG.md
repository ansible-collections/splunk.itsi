# Splunk ITSI Collection Release Notes

**Topics**

- <a href="#v2-0-0">v2\.0\.0</a>
    - <a href="#release-summary">Release Summary</a>
    - <a href="#minor-changes">Minor Changes</a>
    - <a href="#breaking-changes--porting-guide">Breaking Changes / Porting Guide</a>
    - <a href="#bugfixes">Bugfixes</a>
- <a href="#v1-0-1">v1\.0\.1</a>
    - <a href="#release-summary-1">Release Summary</a>
    - <a href="#bugfixes-1">Bugfixes</a>
- <a href="#v1-0-0">v1\.0\.0</a>
    - <a href="#release-summary-2">Release Summary</a>
    - <a href="#minor-changes-1">Minor Changes</a>
    - <a href="#new-plugins">New Plugins</a>
        - <a href="#httpapi">Httpapi</a>
    - <a href="#new-modules">New Modules</a>

<a id="v2-0-0"></a>
## v2\.0\.0

<a id="release-summary"></a>
### Release Summary

This major release drops the <code>ansible\.netcommon</code> dependency\, internalising the utilities the collection actually needs\, and adds support for ansible\-core 2\.21\. The <code>itsi\_glass\_table</code> module now raises an explicit error when the <code>jsonschema</code> package is missing\.

<a id="minor-changes"></a>
### Minor Changes

* Integration tests now use the core <code>httpapi</code> connection plugin instead of <code>ansible\.netcommon\.httpapi</code>\.
* ansible\-core 2\.21 is now supported\. Replaced <code>ansible\.module\_utils\.six\.moves\.urllib\.parse</code> with the Python standard library <code>urllib\.parse</code> in <code>itsi\_correlation\_search</code>\.

<a id="breaking-changes--porting-guide"></a>
### Breaking Changes / Porting Guide

* The <code>ansible\.netcommon</code> collection is no longer a dependency\. The <code>remove\_empties</code> and <code>dict\_diff</code> utilities are now provided locally in <code>splunk\_utils\.py</code>\. Users who need advanced httpapi features \(proxy\, client certificates\, timeouts\) can install <code>ansible\.netcommon</code> separately\.

<a id="bugfixes"></a>
### Bugfixes

* itsi\_glass\_table \- Fail with a clear error when the <code>jsonschema</code> package is not installed instead of silently skipping definition validation\.

<a id="v1-0-1"></a>
## v1\.0\.1

<a id="release-summary-1"></a>
### Release Summary

Release summary for v1\.0\.1

<a id="bugfixes-1"></a>
### Bugfixes

* Added required <code>future imports</code> and <code>\_\_metaclass\_\_ \= type</code> boilerplate to all plugin and module Python files for ansible\-test sanity compliance\.
* Fixed <code>requirements\.txt</code> and remove ansible\-core dependency\.
* Updated README\.md according to Ansible Certified Collections README Template\.

<a id="v1-0-0"></a>
## v1\.0\.0

<a id="release-summary-2"></a>
### Release Summary

Release summary for v1\.0\.0

<a id="minor-changes-1"></a>
### Minor Changes

* Add comprehensive unit tests for <code>ItsiRequest</code> in <code>tests/unit/test\_itsi\_request\.py</code>
* Add integration tests for itsi\_aggregation\_policy and itsi\_aggregation\_policy\_info modules\.
* Add integration tests for itsi\_correlation\_search and itsi\_correlation\_search\_info modules\.
* Add new <code>ItsiRequest</code> class in <code>module\_utils/itsi\_request\.py</code> as the unified HTTP abstraction layer for all ITSI modules\.
* Add new module <code>itsi\_add\_episode\_comments</code> for adding comments to ITSI episodes\.
* Add new module <code>itsi\_aggregation\_policy\_info</code> for querying ITSI aggregation policies by ID\, title\, or listing all\.
* Add new module <code>itsi\_aggregation\_policy</code> for managing ITSI aggregation policies \(create\, update\, delete\)\.
* Add new module <code>itsi\_correlation\_search\_info</code> for querying ITSI correlation searches\.
* Add new module <code>itsi\_correlation\_search</code> for managing ITSI correlation searches \(create\, update\, delete\)\.
* Add new module <code>itsi\_episode\_details\_info</code> for querying ITSI episodes by ID\, listing with filters\, or retrieving a count\.
* Add new module <code>itsi\_glass\_table\_info</code> for querying ITSI Glass Table objects\.
* Add new module <code>itsi\_glass\_table</code> for managing ITSI Glass Table objects \(create\, update\, delete\)\.
* Add new module <code>itsi\_service\_info</code> for querying ITSI Service objects\.
* Add new module <code>itsi\_service</code> for managing ITSI Service objects \(create\, update\, delete\)\.
* Add new module <code>itsi\_update\_episode\_details</code> for updating specific fields of ITSI episodes \(severity\, status\, owner\, instruction\)\.
* Add unit tests for itsi\_aggregation\_policy and itsi\_aggregation\_policy\_info modules\.
* Add unit tests for itsi\_correlation\_search and itsi\_correlation\_search\_info modules\.
* Add validated content for Event\-Driven Ansible \(EDA\) rulebook activation with Splunk ITSI webhook integration\.
* Align all modules to use a unified diff implementation for consistent change detection\.
* Centralize HTTP response status handling in <code>ItsiRequest</code> class\.
* Refactor all ITSI modules to use <code>ItsiRequest</code> instead of the previous standalone functions
* Refactor shared utility functions into module\_utils/itsi\_utils\.py for code reuse\.
* Remove deprecated <code>\_send</code>\, <code>\_send\_request</code>\, and <code>send\_itsi\_request</code> functions
* Standardize return result across all info modules <em class="title-reference">\(changed\, response\)</em>
* Standardize return result across all modules <em class="title-reference">\(changed\, before\, after\, diff\, response\)</em>
* itsi\_aggregation\_policy \- Use dedicated function for handling empty lists in <code>filter\_criteria</code> and <code>breaking\_criteria</code>\.

<a id="new-plugins"></a>
### New Plugins

<a id="httpapi"></a>
#### Httpapi

* splunk\.itsi\.itsi\_api\_client \- HttpApi Plugin for Splunk ITSI\.

<a id="new-modules"></a>
### New Modules

* splunk\.itsi\.itsi\_add\_episode\_comments \- Add comments to Splunk ITSI episodes\.
* splunk\.itsi\.itsi\_aggregation\_policy \- Manage Splunk ITSI aggregation policies\.
* splunk\.itsi\.itsi\_aggregation\_policy\_info \- Get information about Splunk ITSI aggregation policies\.
* splunk\.itsi\.itsi\_correlation\_search \- Manage Splunk ITSI correlation searches\.
* splunk\.itsi\.itsi\_correlation\_search\_info \- Query Splunk ITSI correlation searches\.
* splunk\.itsi\.itsi\_episode\_details\_info \- Read Splunk ITSI notable\_event\_group \(episodes\)\.
* splunk\.itsi\.itsi\_glass\_table \- Manage Splunk ITSI Glass Table objects via itoa\_interface\.
* splunk\.itsi\.itsi\_glass\_table\_info \- Read Splunk ITSI glass table objects via itoa\_interface\.
* splunk\.itsi\.itsi\_service \- Manage Splunk ITSI Service objects via itoa\_interface\.
* splunk\.itsi\.itsi\_service\_info \- Gather facts about Splunk ITSI Service objects via itoa\_interface\.
* splunk\.itsi\.itsi\_update\_episode\_details \- Update specific fields of Splunk ITSI episodes\.
