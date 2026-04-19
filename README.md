# CalcFlip Time Data

**Complete 24-Hour to 12-Hour Time Conversion Reference Dataset**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Data Points](https://img.shields.io/badge/Data%20Points-1%2C440-blue.svg)](https://github.com/calcflip/calcflip-time-data)
[![Military Time](https://img.shields.io/badge/Military%20Time-0000--2359-orange.svg)](https://calcflip.com/military-time)
[![Live Tool](https://img.shields.io/badge/Live%20Tool-CalcFlip.com-brightgreen.svg)](https://calcflip.com)

The most complete open-source time conversion reference dataset available. Every single minute of the 24-hour clock — all **1,440 values** — with 12-hour AM/PM equivalents, military time format, spoken pronunciation, and period classification.

Built and maintained by [CalcFlip](https://calcflip.com) — free instant time converters with no ads and no signup.

---

## What's Inside

| File | Description | Records |
|------|-------------|---------|
| `time-conversions.json` | All 1,440 24h → 12h conversions | 1,440 |
| `military-time.json` | Military time with spoken pronunciation | 1,440 |
| `time-periods.json` | Hour classification by time of day | 24 |
| `special-cases.json` | Midnight, noon, and edge cases | 4 |
| `conversion-rules.json` | The mathematical logic as structured data | 6 |

---

## Quick Start

```bash
# Clone the repo
git clone https://github.com/calcflip/calcflip-time-data.git

# Or fetch just the JSON you need
curl https://raw.githubusercontent.com/calcflip/calcflip-time-data/main/time-conversions.json
```

---

## Data Structure

### time-conversions.json

Every minute of the 24-hour clock with its 12-hour equivalent.

```json
{
  "metadata": {
    "total_records": 1440,
    "format_24h": "HH:MM",
    "format_12h": "H:MM AM/PM",
    "source": "ISO 8601 standard",
    "maintained_by": "CalcFlip.com",
    "last_updated": "2026-04-01"
  },
  "conversions": [
    {
      "time_24h": "00:00",
      "time_12h": "12:00 AM",
      "hour_24": 0,
      "minute": 0,
      "period": "AM",
      "period_name": "Midnight",
      "military": "0000",
      "military_spoken": "Zero Hundred Hours",
      "is_special_case": true,
      "special_note": "Midnight — start of day",
      "url": "https://calcflip.com/time/00-00"
    },
    {
      "time_24h": "12:00",
      "time_12h": "12:00 PM",
      "hour_24": 12,
      "minute": 0,
      "period": "PM",
      "period_name": "Noon",
      "military": "1200",
      "military_spoken": "Twelve Hundred Hours",
      "is_special_case": true,
      "special_note": "Noon — midday",
      "url": "https://calcflip.com/time/12-00"
    },
    {
      "time_24h": "18:00",
      "time_12h": "6:00 PM",
      "hour_24": 18,
      "minute": 0,
      "period": "PM",
      "period_name": "Early Evening",
      "military": "1800",
      "military_spoken": "Eighteen Hundred Hours",
      "is_special_case": false,
      "special_note": null,
      "url": "https://calcflip.com/time/18-00"
    }
  ]
}
```

### military-time.json

All military time codes from 0000 to 2359 with full pronunciation data.

```json
{
  "metadata": {
    "standard": "NATO STANAG 2112",
    "format": "HHMM (no colon)",
    "range": "0000-2359",
    "total_records": 1440
  },
  "military_times": [
    {
      "military": "0000",
      "standard_12h": "12:00 AM",
      "standard_24h": "00:00",
      "spoken_en": "Zero Hundred Hours",
      "spoken_es": "Cero cero cero cero horas",
      "spoken_de": "Null Uhr",
      "spoken_fr": "Zéro heure",
      "spoken_pt": "Zero zero zero zero horas",
      "spoken_nl": "Nul uur",
      "period": "Midnight",
      "url": "https://calcflip.com/military-time/0000"
    },
    {
      "military": "0600",
      "standard_12h": "6:00 AM",
      "standard_24h": "06:00",
      "spoken_en": "Zero Six Hundred Hours",
      "spoken_es": "Cero seiscientas horas",
      "spoken_de": "Sechs Uhr",
      "spoken_fr": "Six heures",
      "spoken_pt": "Zero seiscentas horas",
      "spoken_nl": "Zes uur",
      "period": "Early Morning",
      "url": "https://calcflip.com/military-time/0600"
    },
    {
      "military": "1800",
      "standard_12h": "6:00 PM",
      "standard_24h": "18:00",
      "spoken_en": "Eighteen Hundred Hours",
      "spoken_es": "Dieciocho cero cero horas",
      "spoken_de": "Achtzehn Uhr",
      "spoken_fr": "Dix-huit heures",
      "spoken_pt": "Dezoito horas",
      "spoken_nl": "Achttien uur",
      "period": "Early Evening",
      "url": "https://calcflip.com/military-time/1800"
    }
  ]
}
```

### time-periods.json

Classification of each hour by time of day. Useful for scheduling apps, healthcare systems, and shift planning tools.

```json
{
  "periods": [
    { "hour_24": 0,  "period": "Midnight",       "shift": "Night",    "description": "Start of day. Hospital night shifts. Overnight transport." },
    { "hour_24": 1,  "period": "Night",           "shift": "Night",    "description": "Late night. Minimal activity." },
    { "hour_24": 2,  "period": "Night",           "shift": "Night",    "description": "Deep night. Emergency services active." },
    { "hour_24": 3,  "period": "Night",           "shift": "Night",    "description": "Pre-dawn. Lowest human activity period." },
    { "hour_24": 4,  "period": "Pre-Dawn",        "shift": "Night",    "description": "Night shift end. Bakeries open. Early flights." },
    { "hour_24": 5,  "period": "Early Morning",   "shift": "Morning",  "description": "Dawn. Early morning runs. First trains." },
    { "hour_24": 6,  "period": "Early Morning",   "shift": "Morning",  "description": "Sunrise. Military reveille. Early workers." },
    { "hour_24": 7,  "period": "Morning",         "shift": "Morning",  "description": "Breakfast. School start. Morning commute." },
    { "hour_24": 8,  "period": "Morning",         "shift": "Morning",  "description": "Business hours begin. Hospital day shift." },
    { "hour_24": 9,  "period": "Morning",         "shift": "Morning",  "description": "Peak morning productivity." },
    { "hour_24": 10, "period": "Mid-Morning",     "shift": "Morning",  "description": "Mid-morning. High work activity." },
    { "hour_24": 11, "period": "Late Morning",    "shift": "Morning",  "description": "Pre-lunch. Approaching midday." },
    { "hour_24": 12, "period": "Noon",            "shift": "Afternoon","description": "Midday. Lunch. Peak retail activity." },
    { "hour_24": 13, "period": "Early Afternoon", "shift": "Afternoon","description": "Post-lunch. Afternoon shift begins." },
    { "hour_24": 14, "period": "Afternoon",       "shift": "Afternoon","description": "Afternoon. School pickup in some regions." },
    { "hour_24": 15, "period": "Afternoon",       "shift": "Afternoon","description": "Mid-afternoon. Peak traffic begins." },
    { "hour_24": 16, "period": "Late Afternoon",  "shift": "Afternoon","description": "Late afternoon. School ends. Rush hour." },
    { "hour_24": 17, "period": "Early Evening",   "shift": "Evening",  "description": "Evening commute. Business close." },
    { "hour_24": 18, "period": "Early Evening",   "shift": "Evening",  "description": "6 PM. End of standard business day. Military evening formation." },
    { "hour_24": 19, "period": "Evening",         "shift": "Evening",  "description": "Dinner time. Evening news. Restaurant peak." },
    { "hour_24": 20, "period": "Evening",         "shift": "Evening",  "description": "Evening entertainment. Hospital evening shift." },
    { "hour_24": 21, "period": "Night",           "shift": "Night",    "description": "Late evening. Last trains in many countries." },
    { "hour_24": 22, "period": "Late Night",      "shift": "Night",    "description": "Night. Hospital night shift starts. Late pharmacy close." },
    { "hour_24": 23, "period": "Late Night",      "shift": "Night",    "description": "Late night. Approaching midnight." }
  ]
}
```

### special-cases.json

The four time values that require special handling in any conversion system.

```json
{
  "special_cases": [
    {
      "time_24h": "00:00",
      "time_12h": "12:00 AM",
      "common_name": "Midnight",
      "military": "0000",
      "note": "Start of day. 00:00 is midnight, not 12:00 AM in some informal uses. ISO 8601 defines 00:00 as the start of a calendar day.",
      "common_error": "Writing 12:00 AM as 12:00 midnight causes ambiguity. Use 00:00 in 24h systems.",
      "url": "https://calcflip.com/time/00-00"
    },
    {
      "time_24h": "12:00",
      "time_12h": "12:00 PM",
      "common_name": "Noon",
      "military": "1200",
      "note": "Midday. 12:00 PM is noon. The most commonly confused time value globally.",
      "common_error": "12:00 PM is noon, not midnight. 12:00 AM is midnight.",
      "url": "https://calcflip.com/time/12-00"
    },
    {
      "time_24h": "00:01",
      "time_12h": "12:01 AM",
      "common_name": "One minute after midnight",
      "military": "0001",
      "note": "First minute of a new calendar day.",
      "common_error": "Sometimes confused with 12:01 PM. The period is AM.",
      "url": "https://calcflip.com/time/00-01"
    },
    {
      "time_24h": "23:59",
      "time_12h": "11:59 PM",
      "common_name": "One minute before midnight",
      "military": "2359",
      "note": "Last minute of a calendar day. Last valid military time value.",
      "common_error": "Not 12:59 PM. The period is PM but the hour is 11, not 12.",
      "url": "https://calcflip.com/time/23-59"
    }
  ]
}
```

### conversion-rules.json

The complete mathematical logic of 24-hour to 12-hour conversion as structured data. Use this to implement conversion in any programming language.

```json
{
  "rules": [
    {
      "id": 1,
      "name": "Midnight special case",
      "condition": "hour_24 == 0",
      "result_hour_12": 12,
      "result_period": "AM",
      "example": "00:30 → 12:30 AM",
      "note": "Hour 0 in 24h = Hour 12 AM in 12h"
    },
    {
      "id": 2,
      "name": "Morning hours",
      "condition": "hour_24 >= 1 AND hour_24 <= 11",
      "result_hour_12": "hour_24 (unchanged)",
      "result_period": "AM",
      "example": "09:15 → 9:15 AM",
      "note": "Hours 1-11 stay the same, just add AM"
    },
    {
      "id": 3,
      "name": "Noon special case",
      "condition": "hour_24 == 12",
      "result_hour_12": 12,
      "result_period": "PM",
      "example": "12:00 → 12:00 PM",
      "note": "Hour 12 in 24h = Hour 12 PM in 12h"
    },
    {
      "id": 4,
      "name": "Afternoon and evening hours",
      "condition": "hour_24 >= 13 AND hour_24 <= 23",
      "result_hour_12": "hour_24 - 12",
      "result_period": "PM",
      "example": "18:00 → 6:00 PM",
      "note": "Subtract 12 from the hour, add PM"
    },
    {
      "id": 5,
      "name": "Minutes rule",
      "condition": "always",
      "result": "minutes never change",
      "example": "14:37 → 2:37 PM",
      "note": "Minutes are identical in both systems"
    },
    {
      "id": 6,
      "name": "Military time format",
      "condition": "always",
      "result": "HHMM with no colon, zero-padded",
      "example": "6:00 AM → 0600, 6:00 PM → 1800",
      "note": "Military time omits the colon and always uses 4 digits"
    }
  ]
}
```

---

## Use Cases

This dataset is used by developers and researchers building:

- **Healthcare scheduling systems** — hospitals and clinics globally use 24-hour time for shift management and medication scheduling
- **Aviation and flight software** — international flight scheduling operates entirely on 24-hour time
- **Military and defense applications** — NATO STANAG 2112 requires standardized time communication
- **Voice assistant applications** — converting spoken time queries to structured time values
- **Shift management tools** — factory, retail, and service industry scheduling
- **International travel apps** — helping users understand local time formats
- **Education platforms** — teaching time conversion to students in 12-hour clock countries
- **Multilingual apps** — spoken military time pronunciation in 6 languages included

---

## Conversion Logic (Code Examples)

### JavaScript

```javascript
function convert24to12(time24h) {
  const [hourStr, minuteStr] = time24h.split(':');
  const hour = parseInt(hourStr, 10);
  const minute = minuteStr;

  if (hour === 0)  return `12:${minute} AM`;
  if (hour === 12) return `12:${minute} PM`;
  if (hour < 12)   return `${hour}:${minute} AM`;
  return `${hour - 12}:${minute} PM`;
}

// Examples
convert24to12('00:00') // → '12:00 AM'
convert24to12('12:00') // → '12:00 PM'
convert24to12('18:30') // → '6:30 PM'
convert24to12('23:59') // → '11:59 PM'
```

### Python

```python
def convert_24_to_12(time_24h: str) -> str:
    hour, minute = map(int, time_24h.split(':'))
    minute_str = f"{minute:02d}"

    if hour == 0:  return f"12:{minute_str} AM"
    if hour == 12: return f"12:{minute_str} PM"
    if hour < 12:  return f"{hour}:{minute_str} AM"
    return f"{hour - 12}:{minute_str} PM"

# Examples
convert_24_to_12("00:00")  # → '12:00 AM'
convert_24_to_12("18:30")  # → '6:30 PM'
convert_24_to_12("23:59")  # → '11:59 PM'
```

### PHP

```php
function convert24to12(string $time24h): string {
    [$hour, $minute] = explode(':', $time24h);
    $hour = (int)$hour;

    if ($hour === 0)  return "12:{$minute} AM";
    if ($hour === 12) return "12:{$minute} PM";
    if ($hour < 12)   return "{$hour}:{$minute} AM";
    return ($hour - 12) . ":{$minute} PM";
}
```

### TypeScript

```typescript
function convert24to12(time24h: string): string {
  const [hourStr, minute] = time24h.split(':');
  const hour = parseInt(hourStr, 10);

  if (hour === 0)  return `12:${minute} AM`;
  if (hour === 12) return `12:${minute} PM`;
  if (hour < 12)   return `${hour}:${minute} AM`;
  return `${hour - 12}:${minute} PM`;
}
```

---

## Most Searched Time Conversions

Based on live search data from [CalcFlip.com](https://calcflip.com/time):

| 24-Hour | 12-Hour | Military | Live Page |
|---------|---------|----------|-----------|
| 00:00 | 12:00 AM | 0000 | [calcflip.com/time/00-00](https://calcflip.com/time/00-00) |
| 12:00 | 12:00 PM | 1200 | [calcflip.com/time/12-00](https://calcflip.com/time/12-00) |
| 13:00 | 1:00 PM  | 1300 | [calcflip.com/time/13-00](https://calcflip.com/time/13-00) |
| 14:00 | 2:00 PM  | 1400 | [calcflip.com/time/14-00](https://calcflip.com/time/14-00) |
| 15:00 | 3:00 PM  | 1500 | [calcflip.com/time/15-00](https://calcflip.com/time/15-00) |
| 16:00 | 4:00 PM  | 1600 | [calcflip.com/time/16-00](https://calcflip.com/time/16-00) |
| 17:00 | 5:00 PM  | 1700 | [calcflip.com/time/17-00](https://calcflip.com/time/17-00) |
| 18:00 | 6:00 PM  | 1800 | [calcflip.com/time/18-00](https://calcflip.com/time/18-00) |
| 19:00 | 7:00 PM  | 1900 | [calcflip.com/time/19-00](https://calcflip.com/time/19-00) |
| 20:00 | 8:00 PM  | 2000 | [calcflip.com/time/20-00](https://calcflip.com/time/20-00) |
| 21:00 | 9:00 PM  | 2100 | [calcflip.com/time/21-00](https://calcflip.com/time/21-00) |
| 22:00 | 10:00 PM | 2200 | [calcflip.com/time/22-00](https://calcflip.com/time/22-00) |
| 23:00 | 11:00 PM | 2300 | [calcflip.com/time/23-00](https://calcflip.com/time/23-00) |

---

## Military Time Pronunciation — 6 Languages

| Military | English | Spanish | German | French | Portuguese | Dutch |
|----------|---------|---------|--------|--------|------------|-------|
| 0000 | Zero Hundred Hours | Cero cero cero cero horas | Null Uhr | Zéro heure | Zero zero horas | Nul uur |
| 0600 | Zero Six Hundred Hours | Cero seiscientas horas | Sechs Uhr | Six heures | Zero seiscentas horas | Zes uur |
| 1200 | Twelve Hundred Hours | Doce cero cero horas | Zwölf Uhr | Douze heures | Doze horas | Twaalf uur |
| 1800 | Eighteen Hundred Hours | Dieciocho cero cero horas | Achtzehn Uhr | Dix-huit heures | Dezoito horas | Achttien uur |
| 2000 | Twenty Hundred Hours | Veinte cero cero horas | Zwanzig Uhr | Vingt heures | Vinte horas | Twintig uur |
| 2359 | Twenty-Three Fifty-Nine Hours | Veintitrés cincuenta y nueve horas | Dreiundzwanzig Uhr neunundfünfzig | Vingt-trois heures cinquante-neuf | Vinte e três horas e cinquenta e nove | Drieëntwintig uur negenenvijftig |

Full pronunciation data for all 1,440 values available in `military-time.json`.

---

## Standards and References

This dataset is built on internationally recognized standards:

- **ISO 8601** — International standard for date and time representation
- **NATO STANAG 2112** — NATO standardization agreement for military time
- **ITU-R TF.460** — UTC and time zone standards used in aviation
- **IEC 60050-111** — International Electrotechnical Vocabulary for time

Live converter at [CalcFlip.com](https://calcflip.com) — used by healthcare workers, military personnel, pilots, travelers, and developers worldwide.

---

## Who Uses 24-Hour Time

Understanding which industries and regions use 24-hour time helps developers target the right audiences:

**Always 24-hour:**
- Military and defense (all NATO countries)
- Aviation and air traffic control (global)
- Maritime navigation
- Hospitals and healthcare (most countries)
- Railway and transport (Europe, Asia)
- Scientific research

**Countries using 12-hour in daily life:**
- United States, Canada, Australia, Philippines, India (informal)

**Countries using 24-hour in daily life:**
- Germany, France, Netherlands, Spain, Portugal, Brazil
- Japan, China, Korea
- Most of Africa, Middle East, Eastern Europe

---

## Related Tools

All live on [CalcFlip.com](https://calcflip.com):

- [Time Converter](https://calcflip.com/time) — All 1,440 24-hour to 12-hour conversions
- [Military Time Converter](https://calcflip.com/military-time) — 0000 to 2359 with pronunciation
- [Roman Numerals](https://calcflip.com/roman-numerals) — Numbers 1 to 3000
- [Temperature Converter](https://calcflip.com/celsius) — Celsius to Fahrenheit and Kelvin
- [Age Calculator](https://calcflip.com/age) — Birth year 1924 to 2024

---

## Contributing

Found an error in the data? Open an issue or submit a pull request.

When contributing:
- Verify against ISO 8601 or NATO STANAG 2112
- Include a source citation
- Test conversion logic against the rules in `conversion-rules.json`

---

## License

MIT License — free to use in personal and commercial projects.

Data sourced from ISO 8601 international standard. Maintained by [CalcFlip.com](https://calcflip.com).

---

## Star This Repo

If this data saved you time, give it a ⭐ — it helps other developers find it.

Built with ❤️ by [CalcFlip](https://calcflip.com) — free instant converters, no ads, no signup.
