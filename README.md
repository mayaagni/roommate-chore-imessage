# Apartment Chore Chart

Automated chore scheduler with SMS reminders for a 4-person apartment.

## Roommates
- **Maya, Sophie, Bri, Alizeh** — all common area chores
- **Maya, Sophie, Bri** — shared bathroom
- **Maya, Bri** — common hallway (included during their vacuum weeks)

## Chore Schedule

| Chore | Frequency | Who |
|-------|-----------|-----|
| Vacuuming (kitchen, entryway, dining, living room) | Weekly | All 4, rotating |
| Wipe-down (counters, dining table, console table, floor spills) | Weekly | All 4, rotating |
| Mopping (kitchen, entryway, dining room) | Monthly (every 4 weeks) | All 4, rotating |
| Stainless steel clean | Monthly (every 4 weeks) | All 4, rotating |
| Bathroom deep clean | Every 2 weeks | Maya, Sophie, Bri |

## Setup

### 1. Install dependencies
```bash
pip install -r requirements.txt
```

### 2. Set environment variables
```bash
export TWILIO_ACCOUNT_SID="your_sid"
export TWILIO_AUTH_TOKEN="your_token"
export TWILIO_PHONE_NUMBER="+15551234567"
```

Or copy `.env.example` to `.env` and fill in your values.

### 3. Update phone numbers
Copy `.env.example` to `.env` and fill in your Twilio creds and roommate phone numbers.

### 4. Preview the schedule
```bash
python main.py preview
```

### 5. Test (dry run)
```bash
python main.py send --dry-run
```

### 6. Send for real
```bash
python main.py send
```

## Automation

A GitHub Actions workflow runs every Thursday at 6pm ET automatically. You can also trigger it manually from the Actions tab.

Add your secrets (Twilio creds + phone numbers) in the repo's Settings > Secrets and variables > Actions.

## Customizing

- **Rotation order**: Edit the `*_ROTATION` lists in `config.py`
- **Message wording**: Edit templates in `messages.py`
- **Start date**: Change `SCHEDULE_START` in `config.py`
- **Add/remove chores**: Add new rotation in `config.py`, template in `messages.py`, logic in `scheduler.py`
