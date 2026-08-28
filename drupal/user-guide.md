# Drupal site - User Guide (Manual)
> A simple skeleton to create a (printed) User Guide (manual) for Drupal Site Administrators (non-developers, non User 1). 

Check https://github.com/theodorosploumis/php-docs to see how this guide is used on a real Drupal project.

## About
Have you ever created a Drupal site and need to provide a **written (printed)** documentation for the site Admins, Managers or Authors? This project is for you. "*How to add a new Page*", "*How to Promote a Node on Front Page*" etc are some of the questions that need answer in a User Guide. 

A lot of administrative tasks in Drupal may have the same UI and similar options. For example when you create a Node by default you see on the form fields like `Title`, `URL Alias`, `Promoted to front page` etc. The documentation for these fields can be generic for every site.

Of course, there is the core module [Tour](https://www.drupal.org/docs/8/core/modules/tour) that can help users with inline popups but this will not work for printed manuals.

---

## See also

- [Drupal.org - User Guide project (asciidoc files)](https://www.drupal.org/project/user_guide)
- [Drupal.org - User Guide PDF](https://www.drupal.org/docs/understanding-drupal/user-guide-e-book-downloads)
- [Drupal.org - Glossary](https://www.drupal.org/docs/user_guide/en/glossary.html)

---

## Requirements
- Use markdown, json or yml files as source.
- Organize User Guide pages in folder structure.
- Use a static generator to build the Guide (hugo, gatsby, grav etc).
- Allow reader to download each User User Guide page or the whole document as pdf, html, odt.

---

## Options and Fields

### Node Options

(Create a a common doc file for these options which are usually the same for every Drupal site. Most of the options appear from contributed modules. The same options may appear for **Media or other custom Content entities**).

- View
- Edit
- Delete
- Create (Add new)
- Publish/Unpublish
- Preview
- Replicate
- Create Revision
- View Revisions
- Revert Revisions
- Compare Revisions

---

### Paragraphs Options
(Create a a common doc file for these options which are usually the same for every Drupal site. Most of the options appear from contributed modules.)

- View
- Edit
- Delete (Remove)
- Create (Add new)
- Preview
- Move up/down (change weight)
- Duplicate
- Collapse
- Add Above

---

### Webform Options
(Create a a common doc file for these options which are usually the same for every Drupal site. These options appear from the webform module.)

- View
- Submit
- Edit
- Delete
- Resend (submit with the existing values)
- Test
- Notes (add administrative notes)

---

### Menu Options
(Create a a common doc file for these options which are usually the same for every Drupal site. These options appear from the core menu module.)

- View menu links
- Add new menu link
- Change weight of menu links
- Edit a menu link
- Delete a menu link
- Enable/Disable a menu link
- Show as expanded
- (Alternative way to alter a menu link)

---

### Node Form Fields

(Create a a common doc file for these options which are usually the same for every Drupal site. Some of the fields appear from contributed modules.)

- Title
- Create Revision
- Menu Settings
- Metatags
- URL Alias
- URL Redirects
- Simple XML Sitemap
- Authored by (author)
- Authored on (created date)
- Promoted to front page
- Sticky at top of lists
- Published
- **CUSTOM FIELDS (eg Paragraph fields, images etc...)**

---

## Templates
- [Page Template](/templates/page.md)
- [Entity Metadata Template](/templates/entity_metadata.md)

---

## TOC
An example of Table of Contents for a Drupal site User Guide.

1. Introduction
   * Table of Content
   * Cover, Date created, Owner, Logos and legal notices
   * Requirements and prior knowledge to use these Guides
2. General
   * Login
   * Reset Password
3. Content: Nodes
   * Manage Nodes (Views page explanation)
   * Node options (Actions explanation)
   * Node form visual guide (View-Mode VS Form 1-1 visual mapping)
   * Paragraph TypeA Fields (View-Mode VS Form 1-1 visual mapping)
4. Content: Media/MyEntity etc
   * Manage (see above)
   * Options (see above)
5. Content: Taxonomy
   * Manage (see above)
   * Options (see above)
6. Content: Blocks
   * (Same as above)
7. Dynamic Pages
   * Views Page A (how it selects data)
   * Views Block B (how it selects data)
8. Forms
   * FormA
     * View FormA Results table
     * Download FormA results
     * Purge (Clean) FormA results
     * Each Result of FormA Actions
9. Menus
   * MenuA
     * Add menu link
     * Edit menu link
     * Delete menu link
     * Change weight of a menu link
     * Disable/Enable a menu link
     * Expand a menu link
10. Settings
    * Clear Caches
    * Performance Settings
    * Google Analytics
    * Global metatags
    * URL Aliases
    * URL Redirects
    * Site Settings
    * System Users
      * Add User
      * Edit User
      * Delete User
11. Appendix
    * Using the CKEditor
    * Using Contextual links module
    * Using Quick Edit module (quickedit)
    * Styleguide: Basic CSS styles (Heading, link, button, list, blockquote, image, embed etc)
    * Styleguide: CKEditor custom styles (with visual mapping)
    * Styleguide: Dynamic Views from real Drupal Entity in several view modes
    * Node Anatomy
    * All data Fields by usage in Entities
    * Paragraph Anatomy
    * Paragraph View-Mode VS Form 1-1 visual mapping (for every type)
    * What is Drupal CMS
    * (Drupal) Terminology/Glossary (eg What are Nodes, Fields, Taxonomy, Blocks, Users, Paragraphs, View Modes, Caches, CKEditor, Accessibility, HTML)
    * Drupal.org documentation links etc

---

## Tips
- Do not change the official Drupal terminology. Eg use the word "Node" for content pages. Let your readers learn about Drupal.
- Try to use the default Drupal 8.x admin theme (Seven) or a subtheme based on this. It seems that Seven has the best (UX & UI) support for all the contributed modules. This will make also the screenshots reusable across projects.
- Browser used for screenshots should not have plugins enabled that may affect styling or inputs (eg the LastPass plugin that adds buttons on input)
- Avoid keywords and phrases that are too specific. This will make the manuals reusable.
- Make the texts easy to replace with a simple search and replace process.
- Screenshots should contain only the Main Content region (not sidebars etc) except if you use these regions on the Node Forms.
- Screenshots should not contain the Admin Toolbar or other non related UI elements except if needed.
- Screenshots should use a small - medium device width (eg up to 1200px screen).
- Screenshots of Forms with too many fields or Admin Pages with too many tasks Tasks should split to additional Guide Pages.
- Take individual Screenshots of each element form to create a more detailed Guide.
- Use `masquerade` Drupal module to become the user you create the manuals for.
- Don't explain everything in screenshots that are not so important or never used by users (eg do not explain all the advanced `google_analytics` module settings).

---

## Appendix

### Entity Metadata Tables

#### Node type

| Entity Type | Machine name | Description | Fields | Form Mode screenshot | View Mode screenshot | Actions | Options |
| ----------- | ------------ | ----------- | ------ | -------------------- | -------------------- | ------- | ------- |
| Node: Page  | page | A static content... | [title](#fields-title), [body](#fields-body) | (IMAGE) | (IMAGE) | [Add New](#actions-add-new), Delete, Edit, Replicate | [Published](#options-published), Author |

#### Node type Actions

| Entity Type | Action | Description | URL | Frontend button | Backend button |
| ----------- | ------ | ----------- | --- | --------------- | -------------- |
| Node: Page   | Add New | Adds a new Node of type Page | /node/add/page | (IMAGE) | (IMAGE) |

#### Node type Options

| Option | Description | Type | Form Mode screenshot |
| ------ | ----------- | ---- | -------------------- |
| Published | Enables/Disables the public access to a node | checkbox | (IMAGE) |

---

### Fields

| Field name | Machine name | Description | Type | Form Mode screenshot | View Mode screenshot | Cardinality | Required |
| ---------- | ------------ | ----------- | ---- | -------------------- | -------------------- | ----------- | -------- |
| title  | label | Node title | textfield | (IMAGE) | (IMAGE) | 1 | Yes |
