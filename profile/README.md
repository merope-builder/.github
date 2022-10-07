# merope-builder

""**m**ak**e** **r**esearch **o**ut**p**uts, **e**asier"

A toolkit of template repositories which automate data access, analysis, result visualisation and compilation of a research paper document.
Depending on the processing time required to run the analyses, these are suitable for execution using github's continuous integration facility (Github actions).

## Why

Imagine you're working on a paper that includes an analysis based on some data from a remote resource. You want to summarise it and maybe present it as a chart. You manually extract the data, build a chart image, set the titles and paste it into your draft, also updating the wording of the methods section to explain which years you used in your study. When you discuss it with your team you decide to modify the time period. What needs to change? The datafile needs to be downloaded or subsetted again, the chart image needs to be updated, its title and caption need to change and the methods wording also needs to change: theres a lot of scope for things to get out of synch.

There are some useful principles from software development which we can take over to research paper management to help us with this kind of situation:

- **Automation** scripting processes with multiple manual steps so that they can be easily repeated
- **Revision control** the use of plain text formats to store information, so that we can see changes as they are applied over the lifetime of the resource
- **Use of variables**: when building software, we extract values that will be used repeatedly to variables, so that if they are modified, they need only be modified once
- **Dependency management**: tools helps us define dependencies between different artifacts (datafiles, summaries, charts, article drafts) and the scripts used to buld them - so that if something changes, all downstream artifacts should also be refreshed
- **Continuous integration**: the definition of build processes that run automatically when a permanent change is posted, in a well-defined environment (rather than a users local machine)

Using **merope**, we would be able to make the same change as described above (altering the time period used in an analysis) by modifying a year parameter in a single datafile. All resources which depend upon this would be re-built automatically, so that you can ensure that all resources remain in synch.

This is a trivial example, but as your research project grows bigger and more complex, it will be worth the initial time investment in setting up a defined process to build it and manage its dependencies.

## Technologies

- Scripting language: Python (though the principle equally suited for R or other scripting languages)
- Document source format: Markdown, YAML metadata (for authors, affiliations etc), mermaid embedded diagrams
- Document compilation: pandoc
- Bibliographic references data format: bibtex
- Dependency management and build automation: make
- Continuous integration: Github actions

## How to use

1. Set up an analysis:
    1. Navigate to [merope-analysis](https://github.com/merope-builder/merope-analysis) and click the "use this template" button. Specify where you want your new analysis repository to be stored.
    1. Modify the new repository to run your own analysis. You can add Python packages in `requirements.txt`
1. Set up a paper:
    1. Navigate to [merope-paper](https://github.com/merope-builder/merope-paper) and click the "use this template" button. Specify where you want your new paper repository to be stored (it should be alongside your analysis repository that you created above).
    1. Modify the new paper repository to refer to the artifacts from your analysis.

Note: your project may be complex, if so you can create multiple analysis repositories, that each create a set of artifacts. You will have to modify your paper repository to refer to these. (details to follow)

## Etymology
*[Merope](https://en.wikipedia.org/wiki/Merope_(Pleiad))* is a figure in Greek myth, one of the [Pleiades](https://en.wikipedia.org/wiki/Pleiades) and the wife of [Sisyphus](https://en.wikipedia.org/wiki/Sisyphus). You can draw your own conclusions about the relevance of Sisyphus to the construction of research outputs, but often when we're fully committed to a difficult and lengthy task, somebody closeby will be able to offer a simpler way.

## Contacts

- [Nicky Nicolson](https://github.com/nickynicolson) ([n.nicolson@kew.org](mailto:n.nicolson@kew.org))
