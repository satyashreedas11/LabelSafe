# Google OAuth Setup for LabelSafe AI


##  Setup Steps (Complete in Order)

### Step 1: Get Your Supabase Anon Key

1. Go to [Supabase Dashboard](https://supabase.com/dashboard)
2. Select your project 
3. Navigate to **Project Settings** (gear icon) → **API**
4. Copy the **anon/public** key (starts with `eyJ...`)
5. Add it to your `.env` file:
   ```
   SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
   ```

### Step 2: Create Web OAuth Client (For Supabase)

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Navigate to **APIs & Services** → **Credentials**
3. Click **+ CREATE CREDENTIALS** → **OAuth client ID**
4. **Application type**: Web application
5. **Name**: LabelSafe AI Web Client
6. **Authorized redirect URIs**:
   ```
   https://---------.supabase.co/auth/v1/callback
   ```
7. Click **CREATE**
8. **IMPORTANT**: Copy the **Client ID** and **Client Secret** - you'll need these in Step 4

### Step 3: Configure Android Deep Link (Already Done ✅)

The Android deep link for OAuth callback has been configured:
- Scheme: `com.labelsafe`
- Host: `login-callback`
- This allows Google to redirect back to your app after authentication### Step 4: Configure Google Provider in Supabase

1. Go to [Supabase Dashboard](https://supabase.com/dashboard)
2. Select your project
3. Navigate to **Authentication** → **Providers**
4. Find **Google** and click to expand
5. **Enable** the toggle
6. Paste the **Client ID** from Step 2
7. Paste the **Client Secret** from Step 2
8. The **Redirect URL** should already be set to:
   ```
   https://----------.supabase.co/auth/v1/callback
   ```
9. Click **Save**

### Step 5: Verify Your .env File

Make sure your `.env` file contains:
```env
SUPABASE_URL=https://qyyxiugkmuxbalwdnrsl.supabase.co
SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...  # Your actual key
```

---

## Testing

1. Run your app:
   ```bash
   flutter run
   ```

2. Navigate to the login screen
3. Click **"Sign in with Google"**
4. Select your Google account
5. You should be redirected to the home screen

---

## Troubleshooting

### Error: "developer_error" or "12501"
- Verify the Android OAuth client has the correct package name
- Verify the SHA-1 fingerprint matches exactly
- Wait 5-10 minutes for Google Cloud settings to propagate

### Error: "Invalid redirect URI"
- Verify the Web OAuth client has the redirect URI
- Check that Google provider is enabled in Supabase

### Error: "Google Sign-In failed: Invalid credentials"
- Verify Web Client ID and Secret are correctly entered in Supabase
- Make sure you didn't swap Client ID and Client Secret

### User signs in but doesn't reach home screen
- Check that `SUPABASE_URL` and `SUPABASE_ANON_KEY` are correct in `.env`
- Restart the app after updating `.env`
- Check logs for authentication errors

---

##  Release Build Setup (Later)

When you're ready to release your app:

1. **Generate release keystore** (if not already done):
   ```bash
   keytool -genkey -v -keystore android/upload-keystore.jks \
     -alias upload -keyalg RSA -keysize 2048 -validity 10000
   ```

2. **Get release SHA-1**:
   ```bash
   keytool -list -v -keystore android/upload-keystore.jks \
     -alias upload | grep SHA1:
   ```

3. **Create another Android OAuth client** in Google Cloud with:
   - Name: LabelSafe AI Android (Release)
   - Package name: `com.labelsafe`
   - SHA-1: (the one from step 2)

4. Test with release build before publishing
