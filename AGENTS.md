# AGENTS.md - Development Guide for xfce-superkey

## Build/Test Commands
- `make` - Build the main executable from xcape.c
- `make clean` - Remove build artifacts
- `make install` - Install system-wide (requires sudo)
- `make uninstall` - Remove installed binary
- No automated test suite. Test manually.
- To test default behavior (launching whiskermenu): `timeout 5s ./xfce-superkey -d`
- To test custom command parsing: `timeout 5s ./xfce-superkey -d -c "your_command_here"`

## Code Style Guidelines
- Language: C (C89/C90 compatible)
- Indentation: 4 spaces, no tabs
- Braces: K&R style (opening brace on same line for functions, new line for blocks)
- Comments: Use `/* */` style, include header blocks with copyright/GPL license
- Naming: snake_case for functions/variables, CamelCase_t for types with _t suffix
- Headers: Group system headers first, then X11 headers, separate with blank lines
- Error handling: Use fprintf(stderr, ...) for errors, exit(EXIT_FAILURE) for fatal errors
- Memory: Always free allocated memory (malloc/free pairs), check for NULL returns
- Threading: Use pthread for background operations
- Debug: Use `if (self->debug)` guards for debug output to stdout

## Dependencies
- Required: libX11, libXtst, pthread
- Build tools: gcc, make, pkg-config