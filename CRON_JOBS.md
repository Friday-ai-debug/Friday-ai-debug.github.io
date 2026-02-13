# Cron Jobs - AI Email Agent Business

**Created:** February 13, 2026

---

## Active Cron Jobs

### 1. Daily Research Session
**Schedule:** 9:00 AM UTC (5:00 PM PHT)
**Script:** `/home/dadofpie/.openclaw/workspace/cron/daily_research.sh`
**Purpose:** Research 3-5 new companies using Marketing AI skill
**Log:** `/home/dadofpie/.openclaw/workspace/cron/logs/research.log`

---

### 2. Daily Outreach Execution
**Schedule:** 2:00 PM UTC (10:00 PM PHT)
**Script:** `/home/dadofpie/.openclaw/workspace/cron/daily_outreach.sh`
**Purpose:** Execute multi-channel outreach campaigns
**Log:** `/home/dadofpie/.openclaw/workspace/cron/logs/outreach.log`

---

### 3. Daily Metrics Collection
**Schedule:** 6:00 PM UTC (2:00 AM PHT)
**Script:** `/home/dadofpie/.openclaw/workspace/cron/daily_metrics.sh`
**Purpose:** Compile daily metrics and generate reports
**Log:** `/home/dadofpie/.openclaw/workspace/cron/logs/metrics.log`

---

### 4. Weekly Strategy Review
**Schedule:** Sunday 8:00 PM UTC (4:00 AM PHT)
**Script:** `/home/dadofpie/.openclaw/workspace/cron/weekly_review.sh`
**Purpose:** Review weekly performance and plan next week
**Log:** `/home/dadofpie/.openclaw/workspace/cron/logs/weekly.log`

---

### 5. Email Monitoring
**Schedule:** Every 15 minutes
**Script:** `/home/dadofpie/.openclaw/workspace/cron/email_monitor.sh`
**Purpose:** Check jarvis.ai.email.agent@gmail.com for inquiries
**Log:** `/home/dadofpie/.openclaw/workspace/cron/logs/email.log`

---

## Cron Job Configuration

```bash
# Daily Research Session (9:00 AM UTC)
0 9 * * * /home/dadofpie/.openclaw/workspace/cron/daily_research.sh >> /home/dadofpie/.openclaw/workspace/cron/logs/cron.log 2>&1

# Daily Outreach Execution (2:00 PM UTC)
0 14 * * * /home/dadofpie/.openclaw/workspace/cron/daily_outreach.sh >> /home/dadofpie/.openclaw/workspace/cron/logs/cron.log 2>&1

# Daily Metrics Collection (6:00 PM UTC)
0 18 * * * /home/dadofpie/.openclaw/workspace/cron/daily_metrics.sh >> /home/dadofpie/.openclaw/workspace/cron/logs/cron.log 2>&1

# Weekly Strategy Review (Sunday 8:00 PM UTC)
0 20 * * 0 /home/dadofpie/.openclaw/workspace/cron/weekly_review.sh >> /home/dadofpie/.openclaw/workspace/cron/logs/cron.log 2>&1

# Email Monitoring (every 15 minutes)
*/15 * * * * /home/dadofpie/.openclaw/workspace/cron/email_monitor.sh >> /home/dadofpie/.openclaw/workspace/cron/logs/cron.log 2>&1
```

---

## Installation Status

### Ready to Install

**Status:** ⏳ PENDING Gaby Approval

**What happens when approved:**
```bash
# Execute as jarvis (not dadofpie, as cron runs independently)
sudo crontab -u jarvis -e << 'EOF'
0 9 * * * /home/dadofpie/.openclaw/workspace/cron/daily_research.sh >> /home/dadofpie/.openclaw/workspace/cron/logs/cron.log 2>&1
0 14 * * * /home/dadofpie/.openclaw/workspace/cron/daily_outreach.sh >> /home/dadofpie/.openclaw/workspace/cron/logs/cron.log 2>&1
0 18 * * * /home/dadofpie/.openclaw/workspace/cron/daily_metrics.sh >> /home/dadofpie/.openclaw/workspace/cron/logs/cron.log 2>&1
0 20 * * 0 /home/dadofpie/.openclaw/workspace/cron/weekly_review.sh >> /home/dadofpie/.openclaw/workspace/cron/logs/cron.log 2>&1
*/15 * * * * /home/dadofpie/.openclaw/workspace/cron/email_monitor.sh >> /home/dadofpie/.openclaw/workspace/cron/logs/cron.log 2>&1
EOF
```

---

## What These Jobs Do

### Daily Research (9 AM)
- Researches 3-5 new companies
- Updates target lists with researched profiles
- Logs to `research.log`

### Daily Outreach (2 PM)
- Executes multi-channel campaigns
- Sends LinkedIn connections
- Sends cold emails
- Posts to Twitter/X
- Logs to `outreach.log`

### Daily Metrics (6 PM)
- Compiles daily statistics
- Generates reports
- Logs to `metrics.log`

### Weekly Review (Sunday 8 PM)
- Analyzes weekly performance
- Identifies top-performing channels
- Updates strategy based on data
- Logs to `weekly.log`

### Email Monitor (Every 15 min)
- Checks jarvis.ai.email.agent@gmail.com
- Categorizes inquiries (AUDIT, START, CALL, Questions)
- Responds immediately with templates
- Logs to `email.log`

---

## Daily Automation Flow

```
9:00 AM → Research starts (3-5 companies)
         → Updates target profiles
         → Logs completion

11:00 AM → Outreach block 1 (5 LinkedIn connections)
         → Logs to outreach.log

11:30 AM → Outreach block 2 (5 cold emails)
         → Logs to outreach.log

12:00 PM → Outreach block 3 (3 Twitter/X posts)
         → Logs to outreach.log

Every 15 min → Email monitor checks
              → Processes new inquiries
              → Responds immediately
              → Logs to email.log

2:00 AM → Daily metrics compilation starts (next day)
            → Compiles all daily stats
            → Generates reports
            → Logs to metrics.log

...continues throughout the day

Sunday 8 PM → Weekly review
                → Analyzes 7 days of data
                → Identifies what works
                → Updates strategy
                → Plans next week
```

---

## Log Locations

All logs stored in: `/home/dadofpie/.openclaw/workspace/cron/logs/`

| Log File | Purpose | Retention |
|-----------|---------|-----------|
| `research.log` | Daily research sessions | 90 days |
| `outreach.log` | Daily outreach execution | 90 days |
| `metrics.log` | Daily metrics collection | 90 days |
| `weekly.log` | Weekly strategy reviews | 52 weeks |
| `cron.log` | Cron job execution | 90 days |
| `email.log` | Email monitoring | 90 days |

---

## Verification Commands

### Check all cron jobs:
```bash
crontab -l
```

### View specific logs:
```bash
# Today's research
tail -20 /home/dadofpie/.openclaw/workspace/cron/logs/research.log

# Today's outreach
tail -20 /home/dadofpie/.openclaw/workspace/cron/logs/outreach.log

# Today's metrics
tail -20 /home/dadofpie/.openclaw/workspace/cron/logs/metrics.log

# Weekly review
tail -50 /home/dadofpie/.openclaw/workspace/cron/logs/weekly.log
```

### Check script status:
```bash
# Test any script manually
/home/dadofpie/.openclaw/workspace/cron/daily_research.sh
```

---

## Blocking Items

### Phase 1: Cron Job Installation
- [x] All 5 scripts created and made executable
- [x] Log directory structure created
- [ ] Install cron jobs (requires Gaby approval)
- [ ] Verify all jobs are running

### Phase 2: Email Monitoring (Requires Gmail App Password)
- [ ] Configure imap-smtp-email skill
- [ ] Implement inquiry categorization
- [ ] Create response templates
- [ ] Set up notification system

### Phase 3: Marketing AI Integration
- [ ] Complete skill implementation
- [ ] Integrate with cron scripts
- [ ] Add company research automation
- [ ] Add LinkedIn/Email/Twitter integration

---

## Next Steps

**For Gaby:**
1. Review automation plan above
2. Approve cron job installation
3. Provide Gmail app password (for email monitoring)

**After approval, I'll:**
1. Install all 5 cron jobs
2. Verify they're running correctly
3. Start automated execution immediately
4. Provide daily progress reports

---

**Remember:** Scheduled automation = consistent execution, no excuses, measurable results.
