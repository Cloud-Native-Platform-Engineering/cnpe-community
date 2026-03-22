# Cloud Native Platform Engineering Working Group Community

The Cloud Native Platform Engineering Working Group Community is a community of practitioners, vendors, and end-users who are interested in the practice of building and operating cloud native platforms. The community is focused on sharing knowledge, best practices, and tools to help organizations build and operate cloud native platforms effectively.

The community is open to anyone who is interested in cloud native platform engineering, regardless of their level of experience or expertise. The community is a place for practitioners to share their experiences, ask questions, and learn from each other.

## Scope

This community is primarily focused on Cloud Native Platform Engineering and support of the practice within the CNCF ecosystem. The community is not focused on any specific technology or vendor, but rather on the practice of building and operating cloud native platforms.

Our members represent many diverse roles and personas, including:

- Platform consumers / end-users
- Platform developers, maintainers, and providers
- Internal service providers
- Project maintainers and contributors
- Specialists in other areas such as security, networking, storage, etc. who are interested in how their work fits into the platform engineering practice

For examples of Platform Personas see: [Platform as a Product: Understanding the Personas]({{< ref "/blog/paap-personas/" >}})

## Community

- Website: 
  - Staging site: <https://cnpe.netlify.app/>
  - Production site (not yet deployed): <https://www.cloudnativeplatforms.com/>
- CNCF Community Page: TBD
- Slack channel: [#platform-engineering](https://cloud-native.slack.com/archives/C020RHD43BP) in [CNCF Slack](https://slack.cncf.io/)
- Mailing list: TBD
- LinkedIn Page: <https://www.linkedin.com/company/cloud-native-platforms/>

## Meetings

Every two weeks on Tuesday at 11:00 ET ([convert to your local
time](https://dateful.com/convert/eastern-time-et?t=11)).

<!-- remove until community resources are restored
Meetings are listed on the [main CNCF calendar](https://www.cncf.io/calendar/)
as well as the [CNCF Community Calendar](https://community.cncf.io/tag-app-delivery/). 
-->

- Agenda and Notes: <https://docs.google.com/document/d/1_smeS9-j-SuHJi0VXjx4g9xiD2-tgqhnlwf5oSMDQgg/edit#>
- Meeting Link: TBD, please check announcments in the Slack channel.
- Recordings of previous meetings:
  - Prior to June 2025: <https://www.youtube.com/watch?v=tr-A_HreMd4&list=PLjNzvzqUSpxKH8X7wNfYZtkH_ARSeeQH0>

## Organizers / Leads / Co-Chairs

(in alphabetical order)

- Atulpriya Sharma (@techmaharaj)
- Colin Griffin (@krumware)
- Chris Plank (@ChrisPlank)
- Humble Devassy Chirammal (@humblec)
- Katie Greenley (@k8tgreenley)

## Committees

In order to effectively support and manage the diverse needs of the community, we have established several committees. Each committee is responsible for specific areas of the community's activities and initiatives.

- TBD

## TOC Liaisons

- TBD

## Emeritus Leads

- Abby Bangser (@abangser)
- Josh Gavant (@joshgav)

## Key Artifacts

See [Artifacts](https://cloudnativeplatforms.com/artifacts/) for a list of key artifacts produced by the community. These include whitepapers, presentations, and other resources that are useful for practitioners and organizations looking to build and operate cloud native platforms.

### Tagging a new version of a whitepaper or artifact

When a whitepaper, glossary, or other versioned artifact is ready for release, follow this process to tag a new version while preserving document history in git.

1. **Merge all draft changes into `latest/`.**
   Ensure the `latest/` folder contains the final content for the version you want to tag.

2. **Create a folder for the new version.**
   For example, if you are tagging `v2`, create a `v2/` folder alongside `latest/`.

3. **Move the file from `latest/` to the new version folder using `git mv`.**
   This preserves the file's commit history on the new version.

   ```sh
   git mv latest/index.md v2/index.md
   ```

4. **Restore the `latest/` file from the previous commit.**
   This keeps `latest/` intact as the working copy for future edits.

   ```sh
   git checkout HEAD~1 -- latest/index.md
   ```

5. **Update frontmatter in both files.**
   - In the new version file (e.g. `v2/index.md`): update the `url` to include the version (e.g. `whitepapers/platforms/v2`), set `toc_hide: true`, and mark the version as `active` in the `versions` block.
   - In `latest/index.md`: add the new version to the `versions` block.

6. **Repeat for translations.**
   Apply the same `git mv` and restore steps to any translated versions of the artifact under the relevant `content/{lang}/` directories.

7. **Commit and push.**

> **Why `git mv` instead of `cp`?** Using `git mv` followed by restoring the original ensures that `git log --follow` traces the full history of the tagged version file back through all prior edits. A simple copy would start the new file's history from scratch.

### Adding new pages

When adding a new page to the English site, create a translation stub in each language directory so that the page is accessible in all languages. Without a stub, translated versions of the site will return a 404 for the new page.

1. Create your new page under `website/content/en/` as usual.

2. For each supported language (`es`, `zh`, `ja`, `ko`, `fr`, `de`), create a matching file with only frontmatter and `outdated: true`:

   ```yaml
   ---
   title: "Same title as the English page"
   outdated: true
   ---
   ```

   For section pages (`_index.md`), also include `list_pages: true`.

3. The `outdated: true` flag tells the site to display the English content with a "Translation Needed" banner, so you don't need to include any body content in the stub.

### Contributing translations

Translations are one of the most impactful ways to contribute. Here's how the translation workflow works:

1. Find a page to translate. Look for files with `outdated: true` and no body content under `website/content/{lang}/` — these are stubs waiting for a translation.

2. Replace the stub with your translated content. Keep the same frontmatter fields (especially `type`, `url`, and `versions` if present) but translate the `title` and `description`. Remove the `outdated: true` line.

3. If the page has already been translated but the English version has been updated since, the file will have `outdated: true` with existing body content. Update the translation to match the current English version and remove `outdated: true`.

4. For adding a completely new language, open a [localization issue](https://github.com/Cloud-Native-Platform-Engineering/cnpe-community/issues/new?template=localization.yml) and follow the checklist there.

## Active Initiatives

The Community helps coordinate specific initiatives that are have benefits for the broader Platform Engineering community. Some of these initiatives are led by the Community, while others may exist under the CNCF Technical Advisory Groups (TAGs)

| Initiative                                                                 | Leads                                                                 | More Information                                                         |
|--------------------------------------------------------------------------------|------------------------------------------------------------------------|----------------------------------------------------------------------|
| [Content Club](https://www.cloudnativeplatforms.com/initiatives/content-club/)   | <https://www.cloudnativeplatforms.com/initiatives/content-club/#leads>       | <https://www.cloudnativeplatforms.com/initiatives/content-club/> |
| [Platform as a Product](https://www.cloudnativeplatforms.com/initiatives/platform-as-a-product/)   | <https://www.cloudnativeplatforms.com/initiatives/platform-maturity-model-assessment/#leads>)       | <https://www.cloudnativeplatforms.com/initiatives/platform-as-a-product/> |
| [Maturity Model Assessment](https://www.cloudnativeplatforms.com/initiatives/platform-maturity-model-assessment/)   | <https://www.cloudnativeplatforms.com/initiatives/platform-maturity-model-assessment/#leads>       | <https://www.cloudnativeplatforms.com/initiatives/platform-maturity-model-assessment/> |
