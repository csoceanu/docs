## TEST: Update ReleasePlan spec

**Status:** Completed

**Changes Made:**
- Renamed `ReleaseGracePeriodDays` to `RetentionDays` in ReleasePlanSpec
- Changed JSON tag from `releaseGracePeriodDays` to `retentionDays`
- Changed default retention from 7 to 14 days
- Added `NotificationRecipients` field (list of email addresses for release event notifications)
- Added `RequireApproval` field (boolean, when true holds releases in pending state until manually approved)

## TEST-E2E-docs: Update stale documentation in docs repo

**Status:** Completed

**Changes Made:**
- Updated `/workspace/modules/releasing/pages/create-release-plan.adoc`:
  - Changed field name from `releaseGracePeriodDays` to `retentionDays` in example YAML (line 38)
  - Updated default value from 7 days to 14 days in field description (line 51)
- Updated `/workspace/modules/testing/pages/integration/snapshots/index.adoc`:
  - Changed field name from `releaseGracePeriodDays` to `retentionDays` in two locations (lines 96, 104)
  - Updated default value from 7 days to 14 days (line 104)
  - Updated prose from "Configure the Grace Period" to "Configure the Retention Period" (line 96)

**Key Context:**
- The code changes were in a separate repository (api/v1alpha1/releaseplan_types.go)
- Three main changes to ReleasePlanSpec:
  1. Field renamed: `ReleaseGracePeriodDays` → `RetentionDays`
  2. Default value changed: 7 → 14 days
  3. Two new fields added: `NotificationRecipients` and `RequireApproval` (not documented yet in user-facing docs)
- The auto-generated API reference file (`modules/reference/pages/kube-apis/release-service.adoc`) was NOT manually updated as it contains a "Generated documentation. Please do not edit." header and should be regenerated from source
- Used the update-docs skill process to systematically identify stale documentation

**For Next Task:**
- The new fields `NotificationRecipients` and `RequireApproval` were added to the API but are not yet documented in user-facing documentation
- If these features are ready for users, consider adding documentation about how to use them
- The auto-generated API reference should be regenerated to reflect all API changes
