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


For a description of each service check out the [services description page]({{site.baseurl}}/services).

I'm open to other pricing structures, including retainer arrangements, discounts might be possible, transitioning to a more permanent role might be possible, let's have a conversation.

Kindly check out [my policy on job interviews](https://blog.markjgsmith.com/2020/11/20/my-policy-on-job-interviews.html).

Please contact me via email markgsmith@gmail.com for enquiries.

To purchase some software services and / or products visit the [payments page](https://payments.markjgsmith.com).

{:refdef: style="text-align:center;margin-top:50px;"}
![Node.js web development technologies]({{site.baseurl}}/assets/images/nodejs-web-development-technologies.png)
{: refdef}
