# GitHub Workflows for Hyde-Hyde Theme

This directory contains GitHub Actions workflows to automatically test and maintain the Hyde-Hyde Hugo theme.

## Workflows

### 🧪 `test-theme.yml` - Main Testing Workflow

**Triggers:** Push to main branches, Pull Requests, Manual dispatch

**Purpose:** Comprehensive testing of the theme functionality

**What it tests:**
- **Multi-version compatibility** - Tests with latest Hugo and several older versions
- **Theme structure validation** - Ensures required files and directories exist
- **Build process** - Verifies the theme builds successfully with the example site
- **SCSS compilation** - Validates that stylesheets compile correctly
- **HTML output validation** - Checks generated HTML for common issues
- **Content types** - Ensures posts, portfolios, and other content render properly
- **Performance checks** - Monitors file sizes and build performance
- **Configuration variations** - Tests with minimal and extended configurations

**Jobs:**
1. `test-theme` - Main testing matrix across Hugo versions
2. `test-theme-config-variations` - Tests different configuration scenarios
3. `lint-and-format` - Code quality and formatting checks

### 🔍 `theme-validation.yml` - Compatibility & Security

**Triggers:** Version tags, Weekly schedule, Manual dispatch

**Purpose:** Long-term compatibility and security validation

**What it checks:**
- **Hugo version compatibility** - Tests across multiple Hugo versions
- **Security scanning** - Looks for potential security issues
- **Documentation validation** - Ensures proper documentation exists
- **Performance benchmarking** - Measures build times and output sizes

**Jobs:**
1. `validate-theme-compatibility` - Cross-version compatibility testing
2. `security-scan` - Security and best practice checks
3. `theme-documentation` - Documentation completeness validation
4. `performance-test` - Performance analysis and benchmarking

### 🔧 `maintenance.yml` - Automated Maintenance

**Triggers:** Monthly schedule, Manual dispatch

**Purpose:** Automated maintenance and dependency checking

**What it does:**
- **Hugo updates** - Checks for new Hugo releases and compatibility
- **Dependency auditing** - Reviews CDN references and external dependencies
- **Code cleanup** - Identifies unused files and potential issues
- **Maintenance reporting** - Generates reports on theme health

**Jobs:**
1. `check-hugo-updates` - Monitor Hugo releases and test compatibility
2. `check-dependencies` - Audit external dependencies and deprecated functions
3. `cleanup-resources` - Identify unused or problematic files

## Usage

### Running Tests Locally

To run similar tests locally, you can use the following commands:

```bash
# Test basic Hugo build
cd exampleSite
hugo --themesDir ../.. --theme hyde-hyde

# Test with minification
hugo --themesDir ../.. --theme hyde-hyde --minify

# Test with different base URL
hugo --themesDir ../.. --theme hyde-hyde --baseURL "https://example.com"
```

### Manual Workflow Triggers

All workflows can be triggered manually through the GitHub Actions interface:

1. Go to the "Actions" tab in your repository
2. Select the workflow you want to run
3. Click "Run workflow"
4. Choose the branch and click "Run workflow"

### Interpreting Results

- ✅ **Green checkmarks** - All tests passed
- ⚠️ **Yellow warnings** - Non-critical issues found (theme still works)
- ❌ **Red failures** - Critical issues that need attention

### Artifacts

When tests fail, the workflows upload artifacts that include:
- Build outputs for debugging
- Compatibility reports
- Performance metrics
- Maintenance reports

## Customization

### Adding New Tests

To add new tests, edit the appropriate workflow file:

1. **Functional tests** → `test-theme.yml`
2. **Compatibility tests** → `theme-validation.yml`
3. **Maintenance checks** → `maintenance.yml`

### Modifying Hugo Versions

Update the matrix strategy in the workflows to test different Hugo versions:

```yaml
strategy:
  matrix:
    hugo-version:
      - 'latest'
      - '0.119.0'
      - 'your-version-here'
```

### Changing Trigger Conditions

Modify the `on:` section of each workflow to change when they run:

```yaml
on:
  push:
    branches: [ main, develop ]  # Add or remove branches
  schedule:
    - cron: '0 0 * * 0'  # Change schedule
```

## Best Practices

1. **Keep workflows updated** - Regularly update action versions (e.g., `actions/checkout@v4`)
2. **Test before merging** - Always run tests on feature branches
3. **Monitor performance** - Watch for increasing build times or file sizes
4. **Review security warnings** - Address any security scan findings
5. **Update Hugo versions** - Test with new Hugo releases when they're available

## Troubleshooting

### Common Issues

1. **SCSS compilation errors** - Ensure Hugo extended version is used
2. **Missing files** - Check that all required theme files exist
3. **Build timeouts** - Consider optimizing large assets or build process
4. **Permission errors** - Verify file permissions are correct

### Getting Help

If workflows fail unexpectedly:

1. Check the workflow logs for specific error messages
2. Review recent changes that might have caused issues
3. Test the build locally to reproduce the problem
4. Check Hugo documentation for breaking changes
