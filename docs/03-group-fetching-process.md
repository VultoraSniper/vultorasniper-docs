## 3. Group Fetching Features

### 3.1 Overview & Differences

| Aspect                | Advanced Fetching                                              | Manual Fetching                                                |
| --------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- |
| **Group Limits**      | No hard limit                                                  | No hard limit                                                  |
| **Detection Methods** | • Text parsing (regex)<br>• Image OCR (PNG/JPEG)               | • Text parsing (regex)                                         |
| **Performance**       | • Real-time processing<br>• Automatic Telegram API rate-limits | • On-demand processing<br>• Subject to Telegram history limits |
| **Use Cases**         | Live monitoring of groups                                      | Manual group addition                                          |

### 3.2 Advanced Group Fetching

When a user has enabled Advanced Fetching (valid session file present), the flow is:

1. **Automatic Group Discovery**

   * Bot retrieves all groups the user belongs to.
   * Displays a numbered list of groups.
2. **Group Selection**

   * User enters the number of the group they want to track.
   * Groups are added to tracking immediately.
3. **Continuous Monitoring**

   * Listens to Telegram API streams for new messages.
   * Parses text and extracts images for contract addresses.
4. **Validation**

   * Confirms each address before alerting.
   * Filters duplicates.
5. **Real-Time Alerts**

   * Notifies user via bot messages.

#### 3.2.1 Tutorial: Setting Up Advanced Fetching

Follow these steps to enable continuous, automatic group monitoring:

**Step 1: Access the Setup**

* During initial onboarding right after `/start`, or at any time via `/settings` → **Advanced Group Tracking**.

**Step 2: Confirm Setup Prompt**
The bot shows:

```
🛠️ Advanced Group Fetching

Group fetching allows you to automatically fetch all the Telegram groups you are a member of.

📚 Learn more about this feature in our documentation.
```

Buttons: ✅ **Yes, Proceed** | ❌ **No, Skip**

* Tap **Yes, Proceed** to continue.

**Step 3: Obtain Your Telegram API Credentials**
To fetch groups directly from Telegram, you need an **API ID** and **API Hash**:

1. Open your browser and go to [my.telegram.org](https://my.telegram.org).
2. Log in with the same phone number you use for this bot.
3. Click **API Development Tools**.
4. Under **Create new application**, fill in any name (e.g., “VultoraSniper”), a short description, and your URL (optional).
5. After creating, you’ll see **App api\_id** and **App api\_hash**.
6. Copy both values.

The bot then prompts:

```
Please send your credentials in the format:
API_ID:API_HASH
Example: 123456:abcdef1234567890abcdef1234567890
```

* Send this line; the bot replies: `✅ API credentials saved! Now enter your phone number...`

**Step 4: Provide Phone Number**
Bot asks:

```
Enter your phone number (with +countrycode, no spaces), e.g. +12345678901
```

* Send your number.
* Bot replies: `✅ Phone number received! A verification code has been sent via Telegram.`

**Step 5: Enter Verification Code**
Bot asks:

```
Please enter the 5-digit code with spaces between each digit.
Example: 1 2 3 4 5
```

* Send code like `1 2 3 4 5`.
* Bot confirms: `✅ Successfully logged in! You can now use advanced group fetching.`

**Step 6: Select Groups**
The bot retrieves your groups and shows:

```
📂 Select a group to track

1. @group1 (Trading Alerts)
2. @project_news (Announcements)
3. @memeslaundry (Fun)
...

💬 Now enter the group number you'd like to track.
🔙 Cancel
```

* Send the number (e.g. `2`) to add that group.
* Bot replies: `✅ Group @project_news added and is now being tracked.`
* To add more, send another number; when finished, tap `🔙 Cancel` or type `/settings`.

Once groups are selected, the bot begins continuous monitoring and real-time contract detection.

### 3.3 Manual Group Fetching

If Advanced mode is not set up, any `/groups manage` → **Add Group** triggers:

1. **Open Group Management**

   * Send `/groups manage`.
2. **Add Group**

   * Bot prompts to forward a message, send group @username, or invite link.
3. **Bot Validation**

   * Validates the group and replies `✅ Group <identifier> added.`
4. **Repeat or Exit**

   * Forward another message or send another identifier to add more, or type `/back` to finish.
