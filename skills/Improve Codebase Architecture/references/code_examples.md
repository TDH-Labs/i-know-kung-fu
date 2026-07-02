# Code Examples for Architecture Improvement

## Identifying a Shallow Module
```typescript
// Bad: Shallow module with complex interface
class UserManager {
  constructor(dbConnection: Connection, logger: Logger, config: Config) {
    // ...
  }
  
  async createUser(
    email: string, 
    password: string, 
    profileData: object,
    options?: {validateEmail?: boolean, sendWelcome?: boolean}
  ): Promise<User> {
    // Complex validation logic
    // Email sending logic
    // Database operations
    // Logging
  }
}
```

## Refactored Deep Module
```typescript
// Good: Deep module with simple interface
class UserManager {
  async createUser(request: CreateUserRequest): Promise<User> {
    // All complex logic hidden inside
  }
}

interface CreateUserRequest {
  email: string;
  password: string;
  profile?: ProfileData;
}
```

## Adapter Example
```typescript
// Clock interface
interface Clock {
  now(): Date;
}

// Production adapter
class SystemClock implements Clock {
  now() { return new Date(); }
}

// Test adapter
class FakeClock implements Clock {
  constructor(private fixedDate: Date) {}
  now() { return this.fixedDate; }
}
```

## AI Prompt Template
```
Explore the codebase architecture and identify:
1. Modules with complex interfaces but little implementation (shallow)
2. Concepts with duplicate implementations
3. Areas where related code is scattered (low locality)

For each candidate found:
- Describe the current architecture
- Explain why it's problematic
- Propose a deeper module design with:
  * A simplified interface
  * Consolidated implementation
  * Improved locality

Engage in a grilling session to refine the solution before implementation.
```

These examples demonstrate the transformation from problematic shallow modules to improved deep modules with clear interfaces and proper separation of concerns.