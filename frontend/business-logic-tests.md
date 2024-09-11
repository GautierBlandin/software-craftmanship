# Test files

Tests on the backend use Jest as the test framework rather than vitest.

Tests are made up of three parts:
- Arrange
- Act
- Assert

We use the object mother pattern when we need to create complex objects for testing purposes.

Avoid using 'should' in test names. Instead, prefer the imperative form.
For example, instead of ```it('should reset to the inherited value if the new value is nullable')```, use ```it('resets to the inherited value if the new value is nullable')```.

Example of a test file:

```typescript
import { describe, expect, it } from 'vitest';
import { InheritanceType, OptionalInherited } from '@nexspec/warehouse-shared-types/src/titles/TitleMetadata/Inherited';
import { isInherited } from './title-inheritance';
import { InheritableMother } from './inheritable-mother';

describe('updateValue', () => {
  it('resets to the inherited value if the new value is nullable', () => {
    const currentValue = InheritableMother.explicit('explicit').withInheritedValue('inherited').build();

    expect(updateValue(undefined, currentValue)).toMatchObject({
      displayValue: 'inherited',
    });
  });

  it('sets explicit value to null when updating with nullable', () => {
    const currentValue = InheritableMother.explicit('explicit').build();

    expect(updateValue(undefined, currentValue)).toMatchObject({
      displayValue: null,
      explicitValue: null,
    });
  });

  it('sets explicit value to non nullable falsy value when updating with falsy value', () => {
    const currentValue = InheritableMother.explicit('explicit').build();

    expect(updateValue(false, currentValue)).toMatchObject({
      displayValue: false,
      explicitValue: false,
    });
  });

  it('sets values to null when there is not any current value and updating with nullable', () => {
    expect(updateValue(undefined, undefined)).toMatchObject({
      displayValue: null,
      explicitValue: null,
    });
  });

  it('overrides the display value with a new explicit value', () => {
    const currentValue = InheritableMother.inherited('inherited').build();

    expect(updateValue('explicit', currentValue)).toMatchObject({
      displayValue: 'explicit',
      explicitValue: 'explicit',
    });
  });

  it('transforms the value if a transform function is provided', () => {
    const currentValue = InheritableMother.explicit({ frameRate: 30, original: true }).build();

    const transform = (newFrameRate: number) => ({ frameRate: newFrameRate, original: true });

    expect(updateValue(50, currentValue, { transform })).toMatchObject({
      displayValue: { frameRate: 50, original: true },
      explicitValue: { frameRate: 50, original: true },
    });
  });

  it('creates an initial object if the current value is undefined', () => {
    expect(updateValue('explicit', undefined)).toMatchObject({
      displayValue: 'explicit',
      explicitValue: 'explicit',
      inherited: {
        type: 'waitingForInheritance',
      },
    });
  });
});

```
