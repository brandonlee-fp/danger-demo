# Check 1: PR Description
warn("Add a description") if github.pr_body.nil? || github.pr_body.empty?

# Check 2: PR Title
warn("Title too short") if github.pr_title.length < 10

# Check 3: PR Labels
warn("Add labels 🏷️") if github.pr_labels.empty?

# Check 4: PR Size
warn("PR is too large") if git.lines_of_code > 500

# Check 5: Documentation
all_changes = git.modified_files + git.added_files

# Only warn if the PR actually contains changes, but NONE of them are the README
warn("Update README") if all_changes.any? && !all_changes.include?("README.md")

# Confirmation
has_warnings = status_report[:warnings].any?
has_failures = status_report[:errors].any?
message("🎉 **Great Job!** This Pull Request passes all standard health checks. Ready for human review!") if !has_warnings && !has_failures
