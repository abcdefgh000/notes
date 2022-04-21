Reference: https://stackoverflow.com/questions/54622606/what-permissions-are-needed-to-delete-a-file-in-unix

We don't need any permission on the file iteself to delete it! (counter intuitive)

We need read, write and execute permission on the parent dir in which the file resides to delete the file!
