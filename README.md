# sudoku-party
a multiplayer sudoku game client + server

messages:
- NEW_PLAYER()
- YOU_ARE(player_id)
- NEW_SESSION(difficulty)
- JOIN_SESSION(session_id)
- CREATED_SESSION(player_id, session_id, state)
- JOINED_SESSION(player_id, session_id, state)
- LEFT_SESSION(session_id, player_id)
- INPUT(session_id, state, player_id): encompasses change in highlight, number entry
- VALIDATE(session_id)
- VALIDATION(session_id, errs)
- FINISHED(session_id)