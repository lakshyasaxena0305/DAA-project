# Log Merger & Compression Assistant (Minimal C++)

A minimal C++ project that:
1. Merges multiple log files into one output file.
2. Compresses the merged file using a simple binary Run-Length Encoding (RLE).

## Project structure

- `src/main.cpp` - main program and core logic
- `CMakeLists.txt` - CMake build file
- `web/` - simple frontend + Node.js API that calls the C++ executable

## Build and run (CMake)

```powershell
cmake -S . -B build
cmake --build build
```

Run example:

```powershell
.\build\Debug\log_assistant.exe merged.log merged.rle log1.txt log2.txt
```

## Build and run (g++)

```powershell
g++ -std=c++17 -O2 -o log_assistant src/main.cpp
.\log_assistant.exe merged.log merged.rle log1.txt log2.txt
```

## Notes

- The compression format is binary and intended for demonstration.
- This is a learning-focused minimal implementation.

## Frontend connection (VS Code)

The frontend uploads log files and sends them to a local Node.js API.
The API runs the C++ executable and returns download links for `merged.log` and `merged.rle`.

1. Build the C++ app first:

```powershell
cmake -S . -B build
cmake --build build
```

2. Start frontend server:

```powershell
cd web
npm install
npm start
```

3. Open in browser:

```text
http://localhost:3000
```

4. Upload one or more logs and click **Merge & Compress**.
