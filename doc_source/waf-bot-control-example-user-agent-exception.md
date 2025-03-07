# AWS WAF Bot Control example: Create an exception for a blocked user agent<a name="waf-bot-control-example-user-agent-exception"></a>

If a bot is being erroneously blocked, you can create an exception by excluding the offending AWS WAF Bot Control rule and then combining the rule label with the exception criteria\. 

The following rule uses the Bot Control managed rule group but changes the rule action for `SignalNonBrowserUserAgent` to count, by excluding it from normal rule group processing\. The signal rule applies its labels as usual to matching requests, but only counts them instead of performing its usual action of block\. 

```
{
  "Name": "AWS-AWSBotControl-Example",
  "Priority": 5,
  "Statement": {
    "ManagedRuleGroupStatement": {
      "VendorName": "AWS",
      "Name": "AWSManagedRulesBotControlRuleSet",
      "ExcludedRules": [
        {
          "Name": "SignalNonBrowserUserAgent"
        }
      ]
    }
  },
  "VisibilityConfig": {
    "SampledRequestsEnabled": true,
    "CloudWatchMetricsEnabled": true,
    "MetricName": "AWS-AWSBotControl-Example"
  }
}
```

The following rule matches against the signal label that the preceding Bot Control excluded rule adds to its matching web requests\. Among the signal requests, this rule blocks all but those that have the user agent that you want to allow\. 

The following rule must run after the preceding Bot Control managed rule group in the web ACL processing order\. 

```
{
	"Name": "match_rule",
    "Statement": {
      "AndStatement": {
        "Statements": [
          {
            "LabelMatchStatement": {
              "Scope": "LABEL",
              "Key": "awswaf:managed:aws:bot-control:signal:non_browser_user_agent"
            }
          },
          {
            "NotStatement": {
              "Statement": {
                "ByteMatchStatement": {
                  "FieldToMatch": {
                    "SingleHeader": {
                      "Name": "user-agent"
                    }
                  },
                  "PositionalConstraint": "EXACTLY",
                  "SearchString": "PostmanRuntime/7.29.2",
                  "TextTransformations": [
                    {
                      "Priority": 0,
                      "Type": "NONE"
                    }
                  ]
                }
              }
            }
          }
        ]
      }
    },
    "RuleLabels": [],
    "Action": {
      "Block": {}
    },
    "VisibilityConfig": {
      "SampledRequestsEnabled": true,
      "CloudWatchMetricsEnabled": true,
      "MetricName": "match_rule"
    }
}
```