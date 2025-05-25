## 3. Group Fetching Features

VultoraSniper offers two distinct methods for monitoring Telegram groups: Advanced and Manual fetching. Each method is designed to suit different user needs and technical preferences.

### 3.1 Overview & Differences

| Aspect                | Advanced Fetching                                              | Manual Fetching                                                |
| --------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- |
| **Group Limits**      | No hard limit                                                  | No hard limit                                                  |
| **Detection Methods** | • Text parsing (regex)<br>• Image OCR (PNG/JPEG)               | • Text parsing (regex)                                         |
| **Performance**       | • Real-time processing<br>• Automatic Telegram API rate-limits | • On-demand processing<br>• Subject to Telegram history limits |
| **Use Cases**         | Live monitoring of groups                                      | Manual group addition                                          |

---

### 3.2 Advanced Group Fetching

When a user has enabled Advanced Fetching (valid session file present), the flow is:

1. **Automatic Group Discovery**  
   - Bot retrieves all groups the user belongs to.  
   - Displays a numbered list of groups.  

2. **Group Selection**  
   - User enters the number of the group they want to track.  
   - Groups are added to tracking immediately.  

3. **Continuous Monitoring**  
   - Listens to Telegram API streams for new messages.  
   - Parses text and extracts images for contract addresses.  

4. **Validation**  
   - Confirms each address before alerting.  
   - Filters duplicates.  

5. **Real-Time Alerts**  
   - Notifies user via bot messages.  

#### 3.2.1 Tutorial: Setting Up Advanced Fetching

Follow these steps to enable continuous, automatic group monitoring:

**Step 1: Access the Setup**  
- During initial onboarding right after `/start`, or at any time via `/settings` → **Advanced Group Tracking**.

**Step 2: Confirm Setup Prompt**  
🛠️ Advanced Group Fetching

Group fetching allows you to automatically fetch all the Telegram groups you are a member of.

📚 Learn more about this feature in our documentation.

markdown
Copy
Edit
- Buttons: ✅ **Yes, Proceed** | ❌ **No, Skip**  
- Tap **Yes, Proceed** to continue.

**Step 3: Obtain Your Telegram API Credentials**  
To fetch groups directly from Telegram, you need an **API ID** and **API Hash**:
1. Go to [my.telegram.org](https://my.telegram.org) and log in.  
2. Click **API Development Tools**.  
3. Under **Create new application**, fill in name, description, and URL.  
4. Copy the generated **App api_id** and **App api_hash**.

Bot prompt:
Please send your credentials in the format:
API_ID:API_HASH
Example: 123456:abcdef1234567890abcdef1234567890

javascript
Copy
Edit
- Send this line; the bot replies: `✅ API credentials saved! Now enter your phone number...`

**Step 4: Provide Phone Number**  
Enter your phone number (with +countrycode, no spaces), e.g. +12345678901

less
Copy
Edit
- Bot replies: `✅ Phone number received! A verification code has been sent via Telegram.`

**Step 5: Enter Verification Code**  
Please enter the 5-digit code with spaces between each digit.
Example: 1 2 3 4 5

markdown
Copy
Edit
- Bot confirms: `✅ Successfully logged in! You can now use advanced group fetching.`

**Step 6: Select Groups**  
Bot shows:
📂 Select a group to track

@group1 (Trading Alerts)

@project_news (Announcements)

@memeslaundry (Fun)
...

💬 Enter the group number you'd like to track.
🔙 Cancel

markdown
Copy
Edit
- Send the number (e.g. `2`) to add that group.  
- Bot replies: `✅ Group @project_news added and is now being tracked.`  
- To add more, send another number; when finished, tap `🔙 Cancel` or type `/settings`.

---

### 3.3 Manual Group Fetching

If Advanced mode is not set up, any `/groups manage` → **Add Group** triggers:

1. **Open Group Management**  
   - Send `/groups manage`.  

2. **Add Group**  
   - Bot prompts to forward a message, or send group @username or invite link.  

3. **Bot Validation**  
   - Validates the group and replies `✅ Group <identifier> added.`  

4. **Repeat or Exit**  
   - Forward another message or send another identifier to add more, or type `/back` to finish.

---

### 3.4 Error Handling & Troubleshooting

#### Common Issues
- **API Credential Errors**  
  - Invalid format: Ensure you’re using the correct `API_ID:API_HASH` format.  
  - Expired credentials: Generate new credentials if verification fails.  
- **Group Access Issues**  
  - Private groups: Requires invite link.  
  - Rate limiting: Bot automatically handles Telegram API limits.  
  - Permission errors: Ensure bot has necessary group permissions.  

#### Troubleshooting Steps
1. Verify API credentials format.  
2. Check group privacy settings.  
3. Ensure proper phone number format.  
4. Wait for rate limits to reset if needed.

---

### 3.5 Best Practices

#### Group Selection
- Prioritize active groups with regular token launches.  
- Monitor group quality and remove inactive ones.  
- Consider group size and activity level.

#### Performance Optimization
- Don’t track too many groups simultaneously.  
- Regularly review and prune tracked groups.  
- Remove groups that aren’t providing value.

---

### 3.6 Security Considerations

- API credentials are stored securely.  
- Session data is encrypted.  
- Regular session verification.  
- Automatic session refresh.  