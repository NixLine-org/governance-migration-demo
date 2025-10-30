# Governance Migration Demo

This repository demonstrates how to use NixLine's reusable workflows to migrate existing governance repositories to NixLine baseline format.

## Overview

This demo repository contains example workflows that show how to:

1. **Test migration compatibility** of any governance repository
2. **Perform actual migration** to generate a NixLine baseline
3. **Handle different output modes** (artifacts, commits, pull requests)

**Important**: This repository doesn't contain sample governance files. Instead, the workflows analyze external governance repositories specified by URL.

## Workflow Usage

### 1. Test Migration Compatibility

`.github/workflows/test-migration.yml` - Tests whether a governance repository is ready for migration

**Usage:**
1. Go to Actions tab
2. Run "Test Governance Migration Compatibility" workflow
3. Provide the governance repository URL
4. Review analysis results in the workflow logs

**What it does:**
- Analyzes repository structure and governance files
- Detects project languages and ecosystems
- Validates migration compatibility
- Provides recommendations for any issues found

### 2. Migrate Governance Repository

`.github/workflows/migrate-to-nixline.yml` - Performs actual migration to create NixLine baseline

**Usage:**
1. Go to Actions tab
2. Run "Migrate Governance Repository to NixLine" workflow
3. Provide governance repository URL and organization details
4. Choose output mode:
   - **artifact**: Downloads ZIP with generated baseline
   - **commit**: Commits baseline directly to this repository
   - **pr**: Creates pull request with baseline changes

**What it generates:**
- Complete NixLine baseline with organization-specific configuration
- Policy packs for all detected governance files
- `.nixline.toml` configuration file
- Migration report with next steps

## Example Governance Repositories

You can test the workflows with any governance repository that contains files like:
- LICENSE
- SECURITY.md
- CODEOWNERS / .github/CODEOWNERS
- .editorconfig
- .pre-commit-config.yaml
- .github/dependabot.yml

## Migration Process

1. **Test First**: Always run the test workflow before migration
2. **Review Results**: Check compatibility and fix any issues
3. **Run Migration**: Use the migrate workflow with desired output mode
4. **Deploy Baseline**: Use generated baseline to create your organization's NixLine baseline repository

## Next Steps

After successful migration:
1. Create your organization's baseline repository using the generated files
2. Customize the baseline for your specific needs
3. Deploy to consumer repositories using NixLine's consumption patterns