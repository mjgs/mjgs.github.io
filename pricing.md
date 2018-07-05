---
title: Pricing
layout: page
permalink: "/pricing/"
---

<table style="width:100%; table-layout:fixed; margin-bottom:50px;">
  <thead>
    <tr style="font-size:18px">
      <th>Services</th>
      <th>Basic</th>
      <th>Standard</th> 
      <th>Premium</th>
    </tr>
  </thead>
  <tbody>
  {% for service in site.data.services %}
    <tr>
      <td>{{ service.name }}</td>
      {% for package in service.packages %}  
      <td>
        <ul style="list-style-type:none; text-align:center;">
          <li>{{ package.description }}</li>
          <li>${{ package.price }}</li>
        </ul>
      </td>
      {% endfor %}
    </tr>
  {% endfor %}
  </tbody>
</table>


For a description of each service check out this [blog post]({{site.baseurl}}/2018/07/04/decription-of-my-freelance-nodejs-software-services.html).

Please contact me via email markgsmith@gmail.com for enquiries.

To purchase some software services visit  the [payments page](https://markjgsmith.com/payments/selection);

{:refdef: style="text-align:center;margin-top:50px;"}
![Node.js web development technologies]({{site.baseurl}}/assets/images/nodejs-web-development-technologies.png)
{: refdef}
