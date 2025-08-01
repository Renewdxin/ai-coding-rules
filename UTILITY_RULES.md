# Utility Rules and Common Patterns

## Reusable Code Libraries

### Validation Patterns
```javascript
// Email validation
const EMAIL_REGEX = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
const validateEmail = (email) => EMAIL_REGEX.test(email);

// Phone number validation (Chinese mobile)
const PHONE_REGEX = /^1[3-9]\d{9}$/;
const validatePhone = (phone) => PHONE_REGEX.test(phone);

// Chinese ID card validation
const ID_CARD_REGEX = /^[1-9]\d{5}(18|19|20)\d{2}((0[1-9])|(1[0-2]))(([0-2][1-9])|10|20|30|31)\d{3}[0-9Xx]$/;
const validateIdCard = (id) => ID_CARD_REGEX.test(id);
```

### Error Handling Patterns
```javascript
// Standard error response format
const createErrorResponse = (code, message, details = null) => ({
  success: false,
  error: { code, message, details },
  timestamp: new Date().toISOString()
});

// Async error wrapper
const asyncHandler = (fn) => (req, res, next) => {
  Promise.resolve(fn(req, res, next)).catch(next);
};

// Retry mechanism
const retryAsync = async (fn, maxRetries = 3, delay = 1000) => {
  for (let i = 0; i < maxRetries; i++) {
    try {
      return await fn();
    } catch (error) {
      if (i === maxRetries - 1) throw error;
      await new Promise(resolve => setTimeout(resolve, delay));
    }
  }
};
```

### Data Transformation Utilities
```javascript
// Deep clone object
const deepClone = (obj) => JSON.parse(JSON.stringify(obj));

// Remove empty values from object
const removeEmpty = (obj) => {
  return Object.fromEntries(
    Object.entries(obj).filter(([_, v]) => v != null && v !== '')
  );
};

// Format currency
const formatCurrency = (amount, currency = 'CNY') => {
  return new Intl.NumberFormat('zh-CN', {
    style: 'currency',
    currency: currency
  }).format(amount);
};
```

## Design Pattern Templates

### Factory Pattern
```javascript
class ComponentFactory {
  static create(type, props) {
    switch (type) {
      case 'button': return new Button(props);
      case 'input': return new Input(props);
      default: throw new Error(`Unknown component type: ${type}`);
    }
  }
}
```

### Observer Pattern
```javascript
class EventEmitter {
  constructor() {
    this.events = {};
  }
  
  on(event, callback) {
    if (!this.events[event]) this.events[event] = [];
    this.events[event].push(callback);
  }
  
  emit(event, data) {
    if (this.events[event]) {
      this.events[event].forEach(callback => callback(data));
    }
  }
}
```

### Strategy Pattern
```javascript
class PaymentProcessor {
  constructor(strategy) {
    this.strategy = strategy;
  }
  
  process(amount) {
    return this.strategy.process(amount);
  }
}

class AlipayStrategy {
  process(amount) {
    // Alipay processing logic
    return { method: 'alipay', amount };
  }
}
```

## Common Constants and Enums

### HTTP Status Codes
```javascript
const HTTP_STATUS = {
  OK: 200,
  CREATED: 201,
  BAD_REQUEST: 400,
  UNAUTHORIZED: 401,
  FORBIDDEN: 403,
  NOT_FOUND: 404,
  INTERNAL_SERVER_ERROR: 500
};
```

### Business Status Enums
```javascript
const ORDER_STATUS = {
  PENDING: 'pending',
  CONFIRMED: 'confirmed',
  SHIPPED: 'shipped',
  DELIVERED: 'delivered',
  CANCELLED: 'cancelled'
};

const USER_ROLES = {
  ADMIN: 'admin',
  USER: 'user',
  MODERATOR: 'moderator'
};
```

## Performance Optimization Utilities

### Debounce and Throttle
```javascript
// Debounce function
const debounce = (func, wait) => {
  let timeout;
  return function executedFunction(...args) {
    const later = () => {
      clearTimeout(timeout);
      func(...args);
    };
    clearTimeout(timeout);
    timeout = setTimeout(later, wait);
  };
};

// Throttle function
const throttle = (func, limit) => {
  let inThrottle;
  return function(...args) {
    if (!inThrottle) {
      func.apply(this, args);
      inThrottle = true;
      setTimeout(() => inThrottle = false, limit);
    }
  };
};
```

### Memoization
```javascript
const memoize = (fn) => {
  const cache = new Map();
  return (...args) => {
    const key = JSON.stringify(args);
    if (cache.has(key)) return cache.get(key);
    const result = fn(...args);
    cache.set(key, result);
    return result;
  };
};
```

## Security Utilities

### Input Sanitization
```javascript
const sanitizeHtml = (str) => {
  const map = {
    '&': '&amp;',
    '<': '&lt;',
    '>': '&gt;',
    '"': '&quot;',
    "'": '&#x27;',
    '/': '&#x2F;'
  };
  return str.replace(/[&<>"'/]/g, (s) => map[s]);
};

const sanitizeFilename = (filename) => {
  return filename.replace(/[^a-zA-Z0-9.-]/g, '_');
};
```

### Token Generation
```javascript
const generateToken = (length = 32) => {
  const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
  let result = '';
  for (let i = 0; i < length; i++) {
    result += chars.charAt(Math.floor(Math.random() * chars.length));
  }
  return result;
};
```

## Logging and Monitoring

### Structured Logging
```javascript
const logger = {
  info: (message, meta = {}) => console.log(JSON.stringify({
    level: 'info',
    message,
    timestamp: new Date().toISOString(),
    ...meta
  })),
  
  error: (message, error = null, meta = {}) => console.error(JSON.stringify({
    level: 'error',
    message,
    error: error?.stack || error,
    timestamp: new Date().toISOString(),
    ...meta
  }))
};
```

### Performance Monitoring
```javascript
const performanceTimer = (name) => {
  const start = performance.now();
  return {
    end: () => {
      const duration = performance.now() - start;
      console.log(`${name} took ${duration.toFixed(2)}ms`);
      return duration;
    }
  };
};
```

## Usage Guidelines

### When to Use Utilities
- Use validation patterns for all user input
- Apply error handling patterns consistently across project
- Implement design patterns when complexity justifies them
- Use performance utilities for expensive operations

### Customization Rules
- Adapt patterns to specific project requirements
- Maintain consistent naming conventions
- Document any modifications to standard patterns
- Test all utility functions thoroughly

### Maintenance
- Keep utility library updated with project needs
- Remove unused utilities to reduce bundle size
- Version control utility changes carefully
- Share useful patterns with team members
