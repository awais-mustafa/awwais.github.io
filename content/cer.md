---
title: "My Google Certification"
dateString: April 2023
weight: 101
tags: ["Certification"]
showToc: false
TocOpen: false
draft: false


cover:
    image: "Certificatio/Coursera-MR4FLUFTP4HX_page-0001-_1_.webp" 
     # display caption under cover
    
---
### My Certification

This certification is issued by Coursera. You can verify its authenticity [here](https://www.coursera.org/account/accomplishments/certificate/MR4FLUFTP4HX).



<!DOCTYPE html>
<html>
  <head>
    <title>My Coursera Certifications</title>
  </head>
  <body>
    <h1>My Coursera Certifications</h1>
    <div id="certifications"></div>
    <script src="script.js">
      const container = document.getElementById('certifications');

fetch('https://api.coursera.org/api/external/certificates.v1?user-ids=YOUR_USER_ID&fields=certificates,links')
  .then(response => response.json())
  .then(data => {
    const certifications = data.elements[0].certificates;

    certifications.forEach(certification => {
      const { name, description, certificateImageUrl, link } = certification;

      const certificationElement = document.createElement('div');
      certificationElement.classList.add('certification');

      const imageElement = document.createElement('img');
      imageElement.src = certificateImageUrl;
      certificationElement.appendChild(imageElement);

      const nameElement = document.createElement('h2');
      nameElement.textContent = name;
      certificationElement.appendChild(nameElement);

      const descriptionElement = document.createElement('p');
      descriptionElement.textContent = description;
      certificationElement.appendChild(descriptionElement);

      const linkElement = document.createElement('a');
      linkElement.href = link.url;
      linkElement.textContent = 'View Certificate';
      certificationElement.appendChild(linkElement);

      container.appendChild(certificationElement);
    });
  });

      </script>
  </body>
</html>

