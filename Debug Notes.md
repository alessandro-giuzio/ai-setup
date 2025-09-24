
# Debug Notes

## 🚨 Supabase Auth Error
**Problem:** Login callback returning `null`.  
**Solution:** Added `redirectTo` param in Supabase settings:

```javascript
supabase.auth.signInWithOtp({
  email,
  options: {
    redirectTo: "https://myapp.com/home"
  }
});
```

✅ Fixed on March 18, 2025
