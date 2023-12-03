# <span id="tjidtitle">Organization Structure Module</span>

<div>Technologies: <span id="tjidtechs">Yii2, MySQL, Treant.js</span></div>
<br />

I created this module because i realized how crucial it is, it serves as the foundation for other modules. In a company where its framework is integral to various business processes, maintaining this tree-like type of data, connecting elements as parents, children, and siblings becomes critical. Other modules like leave permissions, reporting, and budgeting (which i've developed and will be explained separately) will greatly benefit from this organizational structure module. Let's dive deeper into an explanation of this module. This module was developed on top of Yii2 PHP framework, MySQL database, and Treant.js library.

First, let's take a look at the ER Diagram. It involves 4 main tables :<br />
<p align="center">
<img width="60%" alt="erd" src="https://github.com/tambunjb/organization-structure-module/assets/22196181/46a4d9c5-77ec-4c84-ad7e-b638d6df31b1">
</p>
1. 'instansi' (organization): serves as the core element, containing all the structures within an organization.<br />
2. 'struktur_jabatan' (role/node): functions like nodes in a tree data structure, representing higher-level roles in this setup.<br />
3. 'unit': a way to group roles/nodes.<br />
4. 'pejabat': signifies the many-to-many relationship between roles and employees (using 'pegawai_id/employee_id' as a Foreign Key). In simpler terms, it shows how employees are positioned within this organizational structure, sometimes holding more than one role.<br />
<br />
There are 2 relations between roles and units: one is the 'unit_id' attribute as a Foreign Key in the 'role' table. The other is 'kepala/head' as a Foreign Key in the 'unit' table, signifying the head position within a unit. To create a tree structure within a relational database, we establish a self-relation in 'struktur_jabatan' (role), where a role may have one or no other role as its parent.
<br /><br />

Next, let's explore the frontend of this module :
<br />

Initially, there's an 'instansi' (organization) management view, allowing CRUD operations for organizations. Clicking on an organization's name in the list takes us to the 'struktur_jabatan' (role) view of that specific organization.
<p align="center">
<img width="60%" alt="instansi" src="https://github.com/tambunjb/organization-structure-module/assets/22196181/17c4e356-7274-4966-8f0c-50c64045e3af">
</p>
<br />
Then, there's the 'struktur_jabatan' (role) management, presented as a tree structure with an 'add' button to include roles, making it more user-friendly and intuitive.
<p align="center">
<img width="60%" alt="struktur_jabatan" src="https://github.com/tambunjb/organization-structure-module/assets/22196181/dce25d2a-926d-47e9-97f6-4ab391743c85">
</p>
<br />
Following that, the 'unit' management view is a standard interface for CRUD operations.
<p align="center">
<img width="60%" alt="unit" src="https://github.com/tambunjb/organization-structure-module/assets/22196181/b1da26fb-4734-49bc-ac5a-e74114a43239">
</p>
<br />
Moving on to the 'pejabat' (employee to role) view, it showcases a list of employees with their current or past roles. Additionally, there's a filter feature: red for expired roles, yellow for roles expiring in 2 months, and green for soon-to-be-held roles.
<p align="center">
<img width="60%" alt="pejabat" src="https://github.com/tambunjb/organization-structure-module/assets/22196181/e87a2f24-5a45-4b80-ac71-cd228fe2d209">
</p>
<br />
Finally, there's a more user-friendly way to visualize the organization's structure using the treant.js library. This feature is meant for general users, allowing them to see the organizational structure and the employees currently in specific roles.
<p align="center">
<img width="60%" alt="tree view" src="https://github.com/tambunjb/organization-structure-module/assets/22196181/7a14a645-04a7-43b2-9954-adb408d6ae03">
</p>
<br />
So, that's a breakdown of this organization structure module. In another project, I'll demonstrate how other modules will benefit from and utilize this module.
<br /><br />
