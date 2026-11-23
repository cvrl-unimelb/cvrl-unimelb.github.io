# Editing the CVRL website

Everything can be done in the browser on GitHub. You don't need to install anything.
Every change you save (a "commit") goes live automatically within about 1–2 minutes.

**Live site:** https://cvrl-unimelb.github.io  
**Repository:** https://github.com/cvrl-unimelb/cvrl-unimelb.github.io

---

## 1. How it works (30 seconds)

The pages are templates. The **content** lives in a few plain-text files in the `_data` folder:

| To change…                             | Edit this file                 |
|----------------------------------------|--------------------------------|
| People (faculty, PhD, Master's, alumni) | `_data/people.yml`            |
| Publications                           | `_data/publications.yml`      |
| News (home page "Latest" + News page)  | `_data/news.yml`              |
| Open positions (Join Us page)          | `_data/positions.yml`         |
| Lab email, address, menu, web address  | `_config.yml`                 |
| Research areas text                    | `research.html` (plain HTML)  |
| Home page intro paragraph              | `index.html` (plain HTML)     |
| Photos                                 | upload to `images/people/`    |
| Colours / layout                       | `css/style.css`               |

The header, footer and logos are shared by all pages: change them once (`_includes/`) and every page updates.

## 2. Making an edit

1. Open the repository on GitHub and click the file (e.g. `_data/news.yml`).
2. Click the **pencil icon** (Edit this file) at the top right of the file.
3. Make your change. Each file starts with a short comment explaining its format.
4. Click **Commit changes…**, write a short note (e.g. "Add CVPR 2027 paper"), then click **Commit changes**.
5. Wait 1–2 minutes and refresh the site.

To watch progress or spot a problem, open the **Actions** tab: a green tick means it's live; a red cross means the update failed (see §6). Until it's fixed, the site keeps showing the previous version.

## 3. Common tasks

### Add a news item (`_data/news.yml`)
Copy this block to the top of the list:

```yaml
- date: 2027-03-01
  type: paper          # paper | team | award | event | service
  title: "CVPR 2027 paper accepted"
  text: "\"Paper title\" accepted at **CVPR 2027**."
```
The newest 5 items appear on the home page automatically (change `home_news_count` in `_config.yml`).

### Add a publication (`_data/publications.yml`)
Copy this block to the top of the list:

```yaml
- title: "Paper title"
  authors: "A. Student, B. Azam, N. Akhtar"
  venue: "IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)"
  badge: "CVPR"
  type: conference     # conference | journal | preprint
  year: 2027
  paper: "https://doi.org/..."
  code: ""
  project: ""
```
Papers are grouped by `year` automatically. Lab members' names appear in bold if they're listed under `highlight_authors` in `_config.yml`. Write the name in exactly the same form, e.g. `N. Akhtar`.

### Add a person (`_data/people.yml`)
1. Upload a square photo (ideally 400×400 px, JPG): open the `images/people` folder, then **Add file → Upload files**, then commit.
2. In `_data/people.yml`, copy an existing student entry, paste it at the end of the `phd:` (or `masters:`) list, and change the values. Set `photo:` to the file name you uploaded, e.g. `"jane-doe.jpg"`.

For the first Master's student, replace `masters: []` with `masters:` followed by the entry (same format as PhD).

### Move someone to Alumni
Cut their entry from `phd:` and add a short entry under `alumni:` (replace `alumni: []`):

```yaml
alumni:
  - name: "Jane Doe"
    role: "PhD 2027"
    now: "Research Scientist, Google"
    website: ""
```

### Open or close a position (`_data/positions.yml`)
Set `open: true` or `open: false`, or copy an entry to add a new one.

## 4. Formatting rules for the `.yml` files

- **Indentation matters.** Use spaces, not tabs, and line up new entries exactly like the existing ones.
- Put text in `"double quotes"`. To use a double quote inside the text, write `\"`.
- Each entry starts with `- ` (dash and space).
- Empty fields are written `""` and are simply not shown on the site.
- In `text:` fields you can use `**bold**` and `[link text](https://...)`.

## 5. Giving others edit access

Organisation owners can add members under **cvrl-unimelb → Settings → People → Invite member** (role *Member*), and then under the repository's **Settings → Collaborators and teams**, give them the *Write* role.
If you'd like to review changes before they go live, ask editors to choose **"Create a new branch and start a pull request"** when committing. You can then approve and merge the change.

## 6. If something goes wrong

- **Red cross in Actions:** this is almost always a formatting slip in a `.yml` file (indentation, a missing quote). Open the failed run to see the file and line, then fix it.
- **Undo a change:** open the file, click **History**, open the earlier commit and copy the old text back. Or ask anyone familiar with Git to *revert* the commit.
- **Photo not showing:** check the file name in `people.yml` matches the uploaded file exactly (it is case-sensitive: `Jane.JPG` ≠ `jane.jpg`).

## 7. Web address

The address comes from the repository name `cvrl-unimelb.github.io` under the `cvrl-unimelb` GitHub organisation.
To use a university domain later (e.g. `cvrl.cis.unimelb.edu.au`), ask UoM IT for a CNAME record pointing to `cvrl-unimelb.github.io`. Then add the domain under the repository's **Settings → Pages → Custom domain** and update `url:` in `_config.yml`.

---
Website created by Basim Azam.
