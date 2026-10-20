---
name: styled-components-helper
description: 'Automated guidance and code generation for styled-components, CSS-in-JS patterns, dynamic theme props, and frontend styling optimization. Trigger with "styled components helper", "styled helper", or "styled".'
version: 1.0.0
author: Jeremy Longshore <jeremy@intentsolutions.io>
license: MIT
tags:
  - frontend
  - react
  - css-in-js
  - styled-components
tools:
  - read
  - write
  - edit
  - bash
  - grep
---

# Styled Components Helper

## Overview

This skill provides automated assistance for building, refactoring, and optimizing `styled-components` in React/TypeScript applications.

## When to Use

Activate this skill when:
- Creating reusable UI components using `styled-components`
- Refactoring raw CSS/SCSS into CSS-in-JS models
- Setting up or extending `ThemeProvider` and theme typing
- Optimizing styled-component performance (preventing unnecessary re-renders, avoiding inline style object allocations)

## Instructions

1. **Type Safety & Theme Props**: Ensure all styled components use explicit TypeScript interfaces for custom props (`interface StyledButtonProps { $primary?: boolean }`). Always use transient props (prefixed with `$`) to prevent custom props from leaking onto the underlying DOM nodes.
2. **Theme Access**: Leverage theme props through function interpolation (`${({ theme }) => theme.colors.primary}`) rather than hardcoded colors or sizing.
3. **Component Extension**: Extend existing styled components using `styled(BaseComponent)` instead of duplicating style declarations.
4. **Production Code Output**: Generate modular, clean, and production-ready code blocks adhering to project linting and formatting standards.

## Examples

### Creating a Styled Button with Transient Props

```tsx
import styled, { css } from 'styled-components';

interface ButtonProps {
  $variant?: 'primary' | 'secondary' | 'outline';
  $size?: 'small' | 'medium' | 'large';
}

export const Button = styled.button<ButtonProps>`
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: ${({ theme }) => theme.radii.md};
  font-weight: 600;
  transition: all 0.2s ease-in-out;
  cursor: pointer;

  ${({ $size = 'medium' }) => {
    switch ($size) {
      case 'small':
        return css`
          padding: 6px 12px;
          font-size: 0.875rem;
        `;
      case 'large':
        return css`
          padding: 12px 24px;
          font-size: 1.125rem;
        `;
      default:
        return css`
          padding: 8px 16px;
          font-size: 1rem;
        `;
    }
  }}

  ${({ $variant = 'primary', theme }) =>
    $variant === 'primary' &&
    css`
      background-color: ${theme.colors.primary};
      color: ${theme.colors.white};
      border: none;

      &:hover {
        background-color: ${theme.colors.primaryDark};
      }
    `}
`;
