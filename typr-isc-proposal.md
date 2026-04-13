# ISC Grant Proposal: `typr` — A Type-Safe S3 Code Generator for R Packages

**Applicant:** Fabrice Hategekimana, M.Sc. Computer Science (University of Geneva)
**Project URL:** [github.com/we-data-ch/typr](https://github.com/we-data-ch/typr)
**Requested funding:** $8,000 USD

## The Problem

R's S3 object system is the backbone of thousands of CRAN packages, yet writing correct S3 code remains error-prone and tedious. Developers must manually define constructors, validators, method dispatches, and generics — with no compile-time checks for type consistency. Common mistakes include mismatched class attributes, missing method implementations, and silent type coercion bugs that surface only at runtime. These issues disproportionately affect package authors who want robust, idiomatic S3 architectures but lack tooling to enforce structural correctness before code execution.

## The Plan

We propose to develop **`typr`**, an R package available on CRAN that integrates the TypR transpiler into standard R workflows. TypR is a statically typed language, written in Rust, that compiles concise type declarations into idiomatic S3 R code — constructors, validators, generics, and method implementations — analogous to how `roxygen2` generates documentation from annotations.

The `typr` package will allow users to write `.typr` type definitions (either as standalone files or inline within R scripts), and generate production-ready S3 code with a single function call. The package will ship with a bundled TypR binary (no Rust toolchain required), integrate with `devtools`/`usethis` conventions, and provide RStudio Addin support for seamless adoption.

**Core deliverables:**

The R package itself (`typr`) will provide three main capabilities. First, `typr::generate()` will transpile `.typr` files into R source files within the `R/` directory of a package project. Second, `typr::typr_inline()` will enable inline type definitions directly in R scripts for prototyping and exploration. Third, the package will include pre-built TypR binaries for Linux, macOS, and Windows so that no external toolchain is needed. Additionally, we will deliver a vignette and `pkgdown` site with real-world examples demonstrating how to define typed S3 hierarchies (e.g., a `Shape` type family with `Circle` and `Rectangle` variants), and we will integrate with `usethis::use_typr()` conventions to scaffold TypR-ready package structures.

## The Team

Fabrice Hategekimana is the creator and sole developer of TypR. He holds a Master's in Computer Science from the University of Geneva and works as a certified IT trainer at the Geneva Institute of Technology (Satom IT & Learning Solutions). He maintains the WeData YouTube channel covering R, Rust, and data science tooling, and has practical experience bridging systems programming with the R ecosystem. The TypR project is backed by the WeData Swiss Verein (association).

## Project Milestones

The project is planned over six months. During months one and two, we will build the core R package structure, implement `typr::generate()` with the bundled Rust binary, and write unit tests with `testthat`. In months three and four, we will add inline mode support, the RStudio Addin, cross-platform binary packaging (Linux, macOS, Windows), and `usethis` integration. Months five and six will focus on writing the vignette and `pkgdown` documentation, conducting user testing with R package developers, submitting to CRAN, and publishing a blog post on R-bloggers.

## How Can The ISC Help

The requested $8,000 will fund development time ($6,000 — approximately 150 hours at the contributor's part-time rate), cross-platform CI/CD infrastructure and binary hosting ($1,000), and community outreach including the Posit Community, R-bloggers, and conference lightning talks ($1,000).

## Dissemination

The package will be published on CRAN and announced via R-bloggers, Posit Community, and the WeData YouTube channel (French-language audience). The source code will remain open-source under MIT license on GitHub. We will actively seek feedback from the R package developer community throughout the development process and aim for adoption as a standard tool in the typed-R ecosystem.
