# Data Service Guidelines

# First Iteration

## Main Goal

- Hosting for important datasets where egress costs are a concern and there are no other good alternatives. A User will be able to stream, upload, and delete files in the dataset.
- Core Function
    - Add/Delete a repository and a namespace
    - Add/Delete/ Change manifest data of files
    - Stream files
    - check permission addition & deletion of a repository

## Design Principles

- **Granularity:**
    - One repository corresponds to one dataset
    - Namespaces will be utilized to manage different versions of the same dataset
        - e.g. when a user creates a different version of a dataset, he/she/they will be creating a new namespace and commit changes in that namespace
- **File management**
    - Uploads include the addition of the physical file and the addition of file in the metadata
    - However, deletions are only reflected on metadata. The physical files will still be in the object storages.
    - Only Addition and Deletion files will be tracked down. Update of individual files won’t be tracked.
- **Metadata Management**: Croissant metadata for each file should be managed and accessed manually by the users
- **Hash Function:**
    - Datasets, hashes, and commits are identified and accessed by their respective hash UIDs
- **Authorization / Permission Management:**
    - Permission is managed only for critical function such as deleting a repository
        - hardcoded X-API-KEY will be used for the critical functions
    - Anonymous writes and updates are allowed for the first iteration
- **File Usage:**
    - Stream use cases are only considered - no download or clone of the entire dataset
    - This is due to the egress cost

# Items for Future Iterations
- **File Management:**
    - Uploads include the addition of the physical file and the addition of file in the metadata

- **Git Operations:**
    - Branch Management
    - Diff / Merge
- **Metadata Management**
    - CRUD of each file metadata through APIs
- **Authorization & Authentication**
    - OAuth2 through Github accounts
    - Specified permission management for each user where each user will be allowed to manage their namespace, and branch


# Hosting the Swagger UI Documentation
The document is hosted using Github Pages. 

1. Change the `swagger.yaml` file content. 

2. Commit and push the changes. 

3. The change will be committed to the Swagger UI at [this page](https://dougieduk.github.io/mlcommons_dataset_api/)