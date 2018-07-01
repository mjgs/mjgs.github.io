---
layout: page
title: Pricing
permalink: /pricing/
---

<table style="width:100%; table-layout:fixed;">
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

