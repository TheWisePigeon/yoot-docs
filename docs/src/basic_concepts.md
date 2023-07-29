# Projects
A project in YOOT terms stands for something like a database. The project is created on the console and inside a project
are Entities which could be compared to SQL tables, finally these Entities contains entries which can be compared to rows in 
an SQL database.

# API keys and permissions
Projects are created on the console, and one or many API keys can be linked to a project. These keys have permissions, set by the project
owner. Yoot API keys have 4 main permissions:

- Read permissions:
  With this permission, the key is authorized to fetch any data contained in the project. That means any entity and any entry contained in any of these entities.
- Create permission:
  With this permission, the key is able to create data in the project. That means the key can be used to create entities and insert entries in any entities.
- Write permission:
  Slightly different from the Create permission, this one allows the key to modify existing data in the project. A key with Create permission can create data but not 
  modify that data. A key with only Write permission can modify data but can not create any new data
- Delete permission:
  This one's name speaks for itself. With this permission the key is able to delete existing data in the project.

Note that the Read permission is always granted by default to the key and can not be removed

# API calls authentication
Every request made to the YOOT API must contain a valid API key in it's Authorization header. Head over to the next page
to learn more about the different endpoints and how to use the API overall
