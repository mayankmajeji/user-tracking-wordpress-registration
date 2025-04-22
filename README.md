# WordPress User Registration Logger

A comprehensive WordPress user registration logging system that captures detailed information about new user registrations and tracks IP usage.

## Features

### 1. User Registration Logging
- Automatically logs extensive data when a new user registers
- Stores data as user meta for each registration
- Tracks login count for each user

### 2. Captured Data Points
- **Basic Information**
  - Timestamp
  - IP Address
  - User Agent
  - Referrer URL

- **Request Details**
  - Request Method (GET/POST)
  - Request URI
  - Query String
  - POST Data
  - GET Data

- **Client Information**
  - Cookies
  - HTTP Headers
  - Session Data
  - IP Geolocation
  - Content Type
  - Authorization Headers
  - TLS Version

- **User Environment**
  - JavaScript Status
  - Language Preferences
  - Timezone Offset
  - Screen Resolution
  - Email Domain

### 3. IP Usage Tracking
- Tracks repeated usage of IP addresses
- Maintains count of registrations per IP
- Useful for detecting potential abuse

## Usage

### Installation
1. Add the code to your theme's `functions.php` or a custom plugin
2. The logging system will automatically activate for new registrations

### Accessing Logged Data
```php
// Get user's login count
$login_count = get_user_meta($user_id, 'maverick_login_count', true);

// Get user's registration log
$registration_log = get_user_meta($user_id, 'maverick_login_log', true);

// Get IP usage count
$ip_count = get_option("maverick_ip_count_$ip");
```

## Data Structure

### Login Log Data
```php
$log_data = [
    'Timestamp'          => 'YYYY-MM-DD HH:MM:SS',
    'IP'                 => 'User IP Address',
    'User Agent'         => 'Browser/Device Information',
    'Referrer'          => 'Registration Page URL',
    'Request Method'     => 'GET/POST',
    'Request URI'        => 'Registration Endpoint',
    'Query String'       => 'URL Parameters',
    'POST Data'          => 'Form Data',
    'GET Data'          => 'Query Parameters',
    'Cookies'           => 'Active Cookies',
    'Headers'           => 'HTTP Headers',
    'Session Data'      => 'PHP Session',
    'IP Geolocation'    => 'IP Address',
    'Content-Type'      => 'Request Content Type',
    'Authorization'     => 'Auth Headers',
    'TLS Version'       => 'SSL/TLS Version',
    'Execution Time'    => 'Processing Time',
    'JavaScript Enabled'=> 'Yes/No/Unknown',
    'Language'          => 'Browser Language',
    'Timezone Offset'   => 'Client Timezone',
    'Screen Resolution' => 'Client Screen Size',
    'Email Domain'      => 'Registration Email Domain',
    'Repeated IP Usage' => 'IP Usage Count'
];
```

## Security Considerations

- Sensitive data in POST/GET arrays should be sanitized before logging
- Consider GDPR compliance when storing user data
- Implement data retention policies
- Consider database size impact with large user bases

## Functions

### `maverick_register_add_meta($user_id)`
- Triggered on user registration
- Logs registration data
- Sets initial login count

### `maverick_check_ip_repeat($ip)`
- Tracks IP address usage
- Returns count of previous registrations from IP
- Updates IP usage counter

## Requirements
- WordPress 5.0 or higher
- PHP 7.0 or higher
- Sufficient database space for logging

## Notes
- Consider implementing data cleanup routines for old logs
- Monitor database size when using with high-traffic sites
- Review logged data periodically for security patterns
- Consider adding data export/deletion capabilities for GDPR compliance

## Support
For issues or questions, please contact the development team or create an issue in the repository. 
