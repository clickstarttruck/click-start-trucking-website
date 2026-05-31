# AI Browser Prompt: Fix A2P 10DLC SMS Compliance Issues
# Site: https://clickstarttruck.com
# Repository: clickstarttruck/click-start-trucking-website
# Generated: 2026-05-27
# Purpose: Resolve all outstanding SMS compliance gaps identified during
#          A2P 10DLC / The Campaign Registry (TCR) pre-submission audit.

---

## CONTEXT

You are an AI browser agent with access to edit the source files of the
Click Start Trucking website hosted on GitHub Pages. The site was audited
against CTIA and TCR A2P 10DLC compliance requirements. Four issues were
found. Your task is to open each affected file in the GitHub web editor,
apply the exact code changes described below, and commit each change with
the provided commit message. Do not change anything beyond what is
specified. After all edits are committed, verify the live site reflects
the changes by navigating to the affected pages.

---

## ISSUE 1 — Consolidate Dual Consent Blocks on /opt-in page
**File:** `opt-in.html`
**Priority:** HIGH — Dual overlapping consent statements can confuse TCR
reviewers about whether consent is checkbox-based or form-submission-based.

### What to do:
Navigate to:
https://github.com/clickstarttruck/click-start-trucking-website/blob/main/opt-in.html

Open the file editor. Locate the TWO separate SMS consent disclosure
blocks that currently appear below the CDL Class dropdown:

BLOCK 1 (checkbox label — KEEP THIS, but update text as shown below):
```html
<label class="sms-consent-label">
  <input type="checkbox" name="sms_consent" value="yes" required>
    I agree to receive SMS messages from Click Start Trucking LLC regarding
      my driver application, onboarding reminders, document requests, and
        status updates. Message &amp; data rates may apply. Reply STOP to opt
          out at any time, HELP for help.
          </label>
          ```

          BLOCK 2 (standalone paragraph below — REMOVE THIS ENTIRE BLOCK):
          ```html
          <p class="sms-disclaimer">
            By submitting this form, you consent to receive automated SMS messages
              from Click Start Trucking LLC. You can reply <strong>STOP</strong> to
                unsubscribe at any time. Message frequency varies. Message &amp; data
                  rates may apply. For help, reply <strong>HELP</strong>.
                  </p>
                  ```

                  ### Replace both blocks with this SINGLE consolidated block:
                  ```html
                  <div class="sms-consent-block">
                    <label class="sms-consent-label">
                        <input type="checkbox" name="sms_consent" value="yes" required>
                            I agree to receive SMS messages from Click Start Trucking LLC
                                regarding my driver application, onboarding reminders, document
                                    requests, and status updates. Message &amp; data rates may apply.
                                        Reply <strong>STOP</strong> to unsubscribe at any time. Reply
                                            <strong>START</strong> to re-subscribe. Reply <strong>HELP</strong>
                                                for assistance, or contact us at
                                                    <a href="mailto:admin@clickstarttruck.com">admin@clickstarttruck.com</a>
                                                        / <a href="tel:4709314436">(470) 931-4436</a>.
                                                            Message frequency varies. Consent is not a condition of any purchase
                                                                or service.
                                                                  </label>
                                                                    <p class="sms-legal-links">
                                                                        Please review our
                                                                            <a href="/privacy-policy">Privacy Policy</a> and
                                                                                <a href="/terms-of-service">Terms of Service</a> before submitting.
                                                                                  </p>
                                                                                  </div>
                                                                                  ```

                                                                                  **Commit message:** `fix: consolidate dual SMS consent blocks into single compliant disclosure on opt-in page`

                                                                                  ---

                                                                                  ## ISSUE 2 — Fix SMS Opt-In Disclosure on Home Page (index.html)
                                                                                  **File:** `index.html`
                                                                                  **Priority:** HIGH — The home page contains a second driver application
                                                                                  form. If it feeds the same SMS list as the /opt-in form, it must display
                                                                                  equally compliant opt-in language including STOP, START, HELP, message
                                                                                  frequency, rates, no-purchase-required, and links to Privacy Policy and
                                                                                  Terms of Service.

                                                                                  ### What to do:
                                                                                  Navigate to:
                                                                                  https://github.com/clickstarttruck/click-start-trucking-website/blob/main/index.html

                                                                                  Open the file editor. Locate the SMS consent section within the
                                                                                  "Driver Application & SMS Opt-In" form on the home page. Find any
                                                                                  existing SMS consent label or disclaimer text in that form.

                                                                                  ### Replace the existing SMS consent area in the home page form with:
                                                                                  ```html
                                                                                  <div class="sms-consent-block">
                                                                                    <label class="sms-consent-label">
                                                                                        <input type="checkbox" name="sms_consent" value="yes" required>
                                                                                            I agree to receive SMS messages from Click Start Trucking LLC
                                                                                                regarding my driver application, onboarding reminders, document
                                                                                                    requests, and status updates. Message &amp; data rates may apply.
                                                                                                        Reply <strong>STOP</strong> to unsubscribe at any time. Reply
                                                                                                            <strong>START</strong> to re-subscribe. Reply <strong>HELP</strong>
                                                                                                                for assistance, or contact us at
                                                                                                                    <a href="mailto:admin@clickstarttruck.com">admin@clickstarttruck.com</a>
                                                                                                                        / <a href="tel:4709314436">(470) 931-4436</a>.
                                                                                                                            Message frequency varies. Consent is not a condition of any purchase
                                                                                                                                or service.
                                                                                                                                  </label>
                                                                                                                                    <p class="sms-legal-links">
                                                                                                                                        Please review our
                                                                                                                                            <a href="/privacy-policy">Privacy Policy</a> and
                                                                                                                                                <a href="/terms-of-service">Terms of Service</a> before submitting.
                                                                                                                                                  </p>
                                                                                                                                                  </div>
                                                                                                                                                  ```
                                                                                                                                                  
                                                                                                                                                  **Commit message:** `fix: add full A2P 10DLC compliant SMS consent disclosure to home page form`
                                                                                                                                                  
                                                                                                                                                  ---
                                                                                                                                                  
                                                                                                                                                  ## ISSUE 3 — Add START Keyword to opt-in.html Disclosure
                                                                                                                                                  **File:** `opt-in.html`
                                                                                                                                                  **Priority:** MEDIUM — The Terms of Service mentions that users can
                                                                                                                                                  reply START to re-subscribe, but this keyword is absent from the
                                                                                                                                                  point-of-consent disclosure on the opt-in page itself. TCR best
                                                                                                                                                  practice requires all keyword responses (STOP, START, HELP) be
                                                                                                                                                  disclosed at the opt-in point.
                                                                                                                                                  
                                                                                                                                                  ### Note:
                                                                                                                                                  This is already handled by the replacement block in Issue 1 above
                                                                                                                                                  (START is included in the new consolidated consent block). If Issue 1
                                                                                                                                                  has been completed correctly, no additional change is needed for this
                                                                                                                                                  issue. Verify that the word "START" appears in the consent label on
                                                                                                                                                  the rendered /opt-in page before marking this resolved.
                                                                                                                                                  
                                                                                                                                                  **Verification step:** Navigate to https://clickstarttruck.com/opt-in
                                                                                                                                                  and confirm the visible consent label text includes the phrase
                                                                                                                                                  "Reply START to re-subscribe."
                                                                                                                                                  
                                                                                                                                                  ---
                                                                                                                                                  
                                                                                                                                                  ## ISSUE 4 — Fix Copyright Year Inconsistency
                                                                                                                                                  **Files:** `opt-in.html`, `privacy-policy.html`, `terms-of-service.html`
                                                                                                                                                  **Priority:** LOW — The footer on opt-in, privacy-policy, and
                                                                                                                                                  terms-of-service pages reads "© 2025 Click Start Trucking LLC" while
                                                                                                                                                  the home page reads "© 2026 Click Start Trucking LLC." All pages
                                                                                                                                                  should display the same year for consistency and professionalism.
                                                                                                                                                  
                                                                                                                                                  ### What to do:
                                                                                                                                                  In each of the three files listed above, locate the footer copyright
                                                                                                                                                  line. It will look like:
                                                                                                                                                  
                                                                                                                                                  ```html
                                                                                                                                                  &copy; 2025 Click Start Trucking LLC. All rights reserved.
                                                                                                                                                  ```
                                                                                                                                                  
                                                                                                                                                  Change `2025` to `2026` in all three files so it reads:
                                                                                                                                                  
                                                                                                                                                  ```html
                                                                                                                                                  &copy; 2026 Click Start Trucking LLC. All rights reserved.
                                                                                                                                                  ```
                                                                                                                                                  
                                                                                                                                                  Edit each file separately and commit with the message below.
                                                                                                                                                  
                                                                                                                                                  **Commit message:** `fix: update copyright year from 2025 to 2026 in footer across all pages`
                                                                                                                                                  
                                                                                                                                                  ---
                                                                                                                                                  
                                                                                                                                                  ## POST-FIX VERIFICATION CHECKLIST
                                                                                                                                                  
                                                                                                                                                  After all four issues are committed, navigate to each URL below and
                                                                                                                                                  confirm the following:
                                                                                                                                                  
                                                                                                                                                  ### https://clickstarttruck.com/opt-in
                                                                                                                                                  - [ ] Only ONE SMS consent block exists (no duplicate paragraph below checkbox)
                                                                                                                                                  - [ ] Checkbox is unchecked by default
                                                                                                                                                  - [ ] Consent label text includes: STOP, START, HELP, message frequency,
                                                                                                                                                        message & data rates, no-purchase-required, email, phone number
                                                                                                                                                        - [ ] Privacy Policy and Terms of Service links are present below the checkbox
                                                                                                                                                        - [ ] Footer reads "© 2026 Click Start Trucking LLC"
                                                                                                                                                        
                                                                                                                                                        ### https://clickstarttruck.com (home page form)
                                                                                                                                                        - [ ] SMS consent checkbox is present and unchecked by default
                                                                                                                                                        - [ ] Consent label includes: STOP, START, HELP, message frequency,
                                                                                                                                                              message & data rates, no-purchase-required
                                                                                                                                                              - [ ] Privacy Policy and Terms of Service links are present
                                                                                                                                                              - [ ] Footer reads "© 2026 Click Start Trucking LLC"
                                                                                                                                                              
                                                                                                                                                              ### https://clickstarttruck.com/privacy-policy
                                                                                                                                                              - [ ] Footer reads "© 2026 Click Start Trucking LLC"
                                                                                                                                                              - [ ] Section 3 (SMS Communications) still intact and unchanged
                                                                                                                                                              
                                                                                                                                                              ### https://clickstarttruck.com/terms-of-service
                                                                                                                                                              - [ ] Footer reads "© 2026 Click Start Trucking LLC"
                                                                                                                                                              - [ ] Section 2 (SMS Messaging Terms) still intact and unchanged
                                                                                                                                                              
                                                                                                                                                              ---
                                                                                                                                                              
                                                                                                                                                              ## TCR CAMPAIGN REGISTRATION NOTES
                                                                                                                                                              
                                                                                                                                                              Once all fixes are live, the site will satisfy the following TCR /
                                                                                                                                                              CTIA requirements for A2P 10DLC campaign approval:
                                                                                                                                                              
                                                                                                                                                              - Single, unambiguous point of written consent with affirmative action
                                                                                                                                                              - All required keywords disclosed at opt-in (STOP, START, HELP)
                                                                                                                                                              - Message frequency disclosure at point of consent
                                                                                                                                                              - Message & data rates disclosure at point of consent
                                                                                                                                                              - Consent-not-a-condition-of-purchase statement at point of consent
                                                                                                                                                              - Privacy Policy linked at point of consent
                                                                                                                                                              - Privacy Policy contains dedicated SMS section with opt-out procedures
                                                                                                                                                              - Terms of Service contains dedicated SMS Messaging Terms section
                                                                                                                                                              - No third-party data sharing for SMS (documented in Privacy Policy)
                                                                                                                                                              - Brand identity and contact info present on all pages
                                                                                                                                                              - Consistent, professional presentation across all pages
                                                                                                                                                              
                                                                                                                                                              **Recommended TCR Campaign Type:** Mixed (Recruiting / Notifications)
                                                                                                                                                              **Recommended Use Case Description for TCR Submission:**
                                                                                                                                                              "Click Start Trucking LLC sends SMS messages to CDL driver applicants
                                                                                                                                                              who have provided written opt-in consent via our driver application
                                                                                                                                                              form at clickstarttruck.com/opt-in. Messages include application
                                                                                                                                                              status updates, onboarding instructions, document requests, and
                                                                                                                                                              compliance reminders. Opt-out is supported via STOP keyword at any
                                                                                                                                                              time. No marketing or promotional messages are sent."
                                                                                                                                                              
