---
layout: page
title: Supported Devices
permalink: /devices/
---

This page tracks all devices, supported with Linux or planned to support in the forthcoming feature.

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
  + {{ f }}
{%     endif %}
    + [{{d.model}}]({{d.url | prepend: site.baseurl}})
{%   else %}
{%     assign f = '' %}
  + [{{d.model}}]({{d.url | prepend: site.baseurl}})
{%   endif %}
{% endfor %}
