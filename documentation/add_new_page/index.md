# How to Add a New Page

To add a new page to this documentation:

1. **Create a New Markdown File**: 
   - Navigate to the documentation folder in the repository.
   - Create a new Markdown file (e.g., `index.md`) where you will write the content for your new page.

2. **Edit the Sidebar**:
   - Locate the `_sidebar.md` file in the documentation folder.
   - Add a link to your new page in the sidebar. The format should look like this:

     ```markdown
     - [Page Title](path/to/index.md)
     ```
     Replace `Page Title` with the title you want to appear in the sidebar, and `path/to/new-page.md` with the actual path to your new Markdown file.

3. **Commit and Push the Changes**:
   - Save the changes to the repository by committing and pushing your new file and the updated `_sidebar.md`.

4. **Verify the Changes**:
   - Open your Docsify site in a browser and ensure the new page appears in the sidebar and displays correctly.

That’s it! You’ve successfully added a new page to the documentation.
