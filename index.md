---
layout: page
title: Supported Devices
redirect_from: /devices/
---

This page tracks all devices, supported with Linux or planned to support in the forthcoming feature.

**NOTE:** these pages are still incomplete and might be incorrect. If you would like to propose a change, don't hesitate to  submit a pull-request against the [LinuxPDA repo](http://github.com/LinuxPDA/linuxpda.github.io/). As the last resort you can drop a note to @lumag or [send an e-mail](mailto:dbaryshkov@gmail.com).

{% assign v = '_' %}
{% assign f = '' %}
{% for d in site.devices %}
{%   if d.vendor != v %}
{%   assign v = d.vendor %}
+ {{ v }}
{%   endif %}
{%   if d.family %}
{%     if d.family != f %}
{%       assign f = d.family %}
{%       assign indent = '  ' %}
  + {{ f }}
{%     endif %}
{%   else %}
{%     assign f = '' %}
{%     assign indent = '' %}
{%   endif %}
{%   assign status = '' %}
{%   if status == '' %}
{%     if d.status-boot != 'Y' %}
{%       assign status = '??' %}
{%     endif %}
{%   endif %}
{%   if status == '' %}{%     assign minus = '0' %}
{%     if d.status-basic != 'Y' and d.status-basic != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-udc != 'Y' and d.status-udc != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-mmc != 'Y' and d.status-mmc != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-pcmcia != 'Y' and d.status-pcmcia != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-display != 'Y' and d.status-display != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     case minus %}{% when '0' %}{% when '1' %}{% assign status = 'C-' %}{% else %}{% assign status = 'D' %}{% endcase %}
{%   endif %}
{%   if status == '' %}{%     assign minus = '0' %}
{%     if d.status-buttons != 'Y' and d.status-buttons != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-touchscreen != 'Y' and d.status-touchscreen != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-suspend != 'Y' and d.status-suspend != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-battery != 'Y' and d.status-battery != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-backlight != 'Y' and d.status-backlight != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     case minus %}{% when '0' %}{% when '1' %}{% assign status = 'B-' %}{% else %}{% assign status = 'C' %}{% endcase %}
{%   endif %}
{%   if status == '' %}{%     assign minus = '0' %}
{%     if d.status-sound != 'Y' and d.status-sound != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-flash != 'Y' and d.status-flash != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-leds != 'Y' and d.status-leds != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-cpufreq != 'Y' and d.status-cpufreq != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     case minus %}{% when '0' %}{% when '1' %}{% assign status = 'A-' %}{% else %}{% assign status = 'B' %}{% endcase %}
{%   endif %}
{%   if status == '' %}{%     assign minus = '0' %}
{%     if d.status-irda != 'Y' and d.status-irda != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-wifi != 'Y' and d.status-wifi != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-bluetooth != 'Y' and d.status-bluetooth != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-gsm != 'Y' and d.status-gsm != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-gps != 'Y' and d.status-gps != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-bootloader != 'Y' and d.status-bootloader != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     if d.status-kexecboot != 'Y' and d.status-kexecboot != 'N/A' %}{% capture minus %}{{ minus | plus: 1 }}{% endcapture %}{% endif %}
{%     case minus %}{% when '0' %}{% when '1' %}{% assign status = 'A' %}{% else %}{% assign status = 'A' %}{% endcase %}
{%   endif %}
{%   if status == '' %}
{%     assign status = 'A+' %}
{%   endif %}
  {{indent}}+ [{{d.model}}]({{d.url | prepend: site.baseurl}}) --- Support status: **{{status}}**
{% endfor %}
