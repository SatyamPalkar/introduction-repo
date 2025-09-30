# Contributing Guidelines

Thank you for your interest in contributing to my projects! This guide will help you understand how to contribute effectively and maintain code quality.

## 🤝 How to Contribute

### 1. Fork and Clone
```bash
# Fork the repository on GitHub
# Clone your fork
git clone https://github.com/YOUR_USERNAME/REPOSITORY_NAME.git
cd REPOSITORY_NAME

# Add upstream remote
git remote add upstream https://github.com/SatyamPalkar/REPOSITORY_NAME.git
```

### 2. Create a Branch
```bash
# Create a new branch for your feature/fix
git checkout -b feature/your-feature-name
# or
git checkout -b fix/issue-description
```

### 3. Make Changes
- Follow the coding standards outlined below
- Write tests for new functionality
- Update documentation as needed
- Ensure all tests pass

### 4. Commit Changes
```bash
# Stage your changes
git add .

# Commit with descriptive message
git commit -m "feat: add new EEG processing feature"
# or
git commit -m "fix: resolve memory leak in data processing"
```

### 5. Push and Create Pull Request
```bash
# Push to your fork
git push origin feature/your-feature-name

# Create a Pull Request on GitHub
```

## 📝 Commit Message Convention

I follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

### Format
```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Types
- **feat**: A new feature
- **fix**: A bug fix
- **docs**: Documentation only changes
- **style**: Changes that do not affect the meaning of the code
- **refactor**: A code change that neither fixes a bug nor adds a feature
- **perf**: A code change that improves performance
- **test**: Adding missing tests or correcting existing tests
- **chore**: Changes to the build process or auxiliary tools

### Examples
```bash
feat(eeg): add real-time signal filtering
fix(ml): resolve model loading issue
docs: update API documentation
test: add unit tests for data preprocessing
```

## 🎨 Coding Standards

### Python Code Style
- Follow [PEP 8](https://www.python.org/dev/peps/pep-0008/)
- Use type hints where possible
- Maximum line length: 88 characters (Black formatter)
- Use meaningful variable and function names

```python
# Good
def process_eeg_signal(signal_data: np.ndarray, 
                      sampling_rate: int = 256) -> np.ndarray:
    """
    Process EEG signal data with filtering and normalization.
    
    Args:
        signal_data: Raw EEG signal data
        sampling_rate: Sampling rate in Hz
        
    Returns:
        Processed signal data
    """
    # Implementation here
    pass

# Bad
def proc(data, sr=256):
    # Implementation here
    pass
```

### JavaScript/TypeScript Code Style
- Follow [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)
- Use TypeScript for type safety
- Use meaningful variable and function names
- Prefer const over let, avoid var

```typescript
// Good
interface EEGData {
  timestamp: number;
  channels: number[];
  samplingRate: number;
}

const processEEGSignal = (data: EEGData): ProcessedData => {
  // Implementation here
};

// Bad
function proc(data) {
  // Implementation here
}
```

### Documentation Standards
- Use docstrings for all functions and classes
- Include type information in docstrings
- Provide examples for complex functions
- Keep README files updated

```python
def calculate_fft(signal: np.ndarray, 
                 window_size: int = 1024) -> np.ndarray:
    """
    Calculate Fast Fourier Transform of the input signal.
    
    Args:
        signal: Input time-domain signal
        window_size: Size of the FFT window
        
    Returns:
        Frequency-domain representation of the signal
        
    Example:
        >>> signal = np.random.randn(1000)
        >>> fft_result = calculate_fft(signal, 512)
        >>> print(fft_result.shape)
        (512,)
    """
    return np.fft.fft(signal, n=window_size)
```

## 🧪 Testing Requirements

### Python Testing
- Use pytest for testing framework
- Aim for >80% code coverage
- Write unit tests for all new functions
- Include integration tests for complex workflows

```python
# test_eeg_processing.py
import pytest
import numpy as np
from src.eeg_processing import process_eeg_signal

def test_process_eeg_signal():
    """Test EEG signal processing function."""
    # Arrange
    test_signal = np.random.randn(1000)
    expected_shape = (1000,)
    
    # Act
    result = process_eeg_signal(test_signal)
    
    # Assert
    assert result.shape == expected_shape
    assert not np.isnan(result).any()
```

### JavaScript/TypeScript Testing
- Use Jest for testing framework
- Write unit tests for components and utilities
- Include snapshot tests for UI components

```typescript
// eeg-processing.test.ts
import { processEEGSignal } from '../src/eeg-processing';

describe('EEG Processing', () => {
  test('should process EEG signal correctly', () => {
    const testSignal = [1, 2, 3, 4, 5];
    const result = processEEGSignal(testSignal);
    
    expect(result).toBeDefined();
    expect(result.length).toBe(testSignal.length);
  });
});
```

## 📋 Pull Request Guidelines

### Before Submitting
- [ ] Code follows style guidelines
- [ ] Tests pass locally
- [ ] Documentation is updated
- [ ] Commit messages follow convention
- [ ] Branch is up to date with main

### PR Description Template
```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
- [ ] Unit tests pass
- [ ] Integration tests pass
- [ ] Manual testing completed

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-review completed
- [ ] Documentation updated
- [ ] No breaking changes (or documented)

## Related Issues
Closes #123
```

## 🐛 Bug Reports

When reporting bugs, please include:

1. **Environment Information**
   - OS and version
   - Python/Node.js version
   - Package versions

2. **Steps to Reproduce**
   - Clear, numbered steps
   - Expected vs actual behavior

3. **Error Messages**
   - Full error traceback
   - Screenshots if applicable

4. **Additional Context**
   - Any relevant configuration
   - Workarounds attempted

## 💡 Feature Requests

When suggesting features:

1. **Problem Description**
   - What problem does this solve?
   - Who would benefit from this feature?

2. **Proposed Solution**
   - Detailed description of the feature
   - Alternative solutions considered

3. **Additional Context**
   - Use cases and examples
   - Potential implementation approach

## 🔍 Code Review Process

### For Contributors
- Address all review comments
- Make requested changes
- Respond to feedback constructively
- Keep PRs focused and small

### For Maintainers
- Review code thoroughly
- Provide constructive feedback
- Test changes locally
- Merge when ready

## 📞 Getting Help

- **GitHub Issues**: For bugs and feature requests
- **Discussions**: For questions and general discussion
- **Email**: For private or urgent matters

## 🏆 Recognition

Contributors will be recognized in:
- CONTRIBUTORS.md file
- Release notes
- Project documentation

## 📜 License

By contributing, you agree that your contributions will be licensed under the same license as the project.

---

*Thank you for contributing! Your efforts help make these projects better for everyone.*
