Control Tower is often used in conjunction with [[AWS Organization]]
to manage and configure a multi account setup.

## Benefits
- Automate setup of [[AWS Organization]]
- Automate policy management using guard rails
- Detect policy violations
- Monitor compliance through dashboard
- Streamline account creation in [[AWS Organization]]

## Guardrails

### Preventive Guardrail
- uses [[AWS Organization]] SCP
- e.g. restrict regions across all accounts

### Detective Guardrail
- uses [[AWS Config]]
- e.g. identify untagged resources

## Further Integration
- [[SNS]] 