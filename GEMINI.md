# AI Video GT

Use the `ai-video-gt` MCP server to work with AI Video GT (aivideogt.com).

- `list_models` and `estimate_cost` show every video and image model with the exact credits for each resolution and clip length. Quote these before generating.
- `find_video_tool` finds a free browser video tool (trim, crop, compress, convert, merge, add music, GIF, screen recorder and more). Files stay on the user's device.
- `generate_video`, `generate_image`, `get_generation`, `list_generations` and `get_account` need the `AIVIDEOGT_API_KEY` environment variable (a Developer API key from aivideogt.com → Account → Developer API). Generations spend the user's credits and failed ones are refunded automatically.
