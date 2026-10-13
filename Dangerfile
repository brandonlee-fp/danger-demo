# Check 1: PR Description
warn("📝 **Missing Description:** Please provide a summary of your changes in the PR description.") if github.pr_body.nil? || github.pr_body.strip.length < 10

# Check 2: PR Title
warn("✏️ **Vague PR Title:** Please make the PR title more descriptive of the actual changes.") if github.pr_title.include?("Update") && github.pr_title.length < 10

# Check 3: PR Labels
warn("🏷️ **Missing Labels:** Please add at least one label (e.g., `bug`, `enhancement`) to this PR.") if github.pr_labels.empty?

# Check 4: PR Size
warn("⚠️ **Large Pull Request:** Consider breaking this down into smaller, focused PRs.") if (git.insertions + git.deletions) > 500

# Check 5: Documentation
warn("📚 **Documentation Check:** You modified source code files but did not update any markdown (`.md`) files.") if git.modified_files.grep(/\.md\/).empty?

# Confirmation
message("🎉 **Great Job!** This Pull Request passes all standard health checks. Ready for human review!") if danger.warnings.empty? && danger.failures.empty?
