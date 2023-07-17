set(proto_files
  gc_api.proto
  gc_change.proto
  gc_ci.proto
  gc_common.proto
  gc_engine.proto
  gc_engine_config.proto
  gc_game_event.proto
  gc_geometry.proto
  gc_rcon.proto
  gc_rcon_autoref.proto
  gc_rcon_remotecontrol.proto
  gc_rcon_team.proto
  gc_referee_message.proto
  gc_state.proto
  grsim_command.proto
  grsim_packet.proto
  grsim_replacement.proto
  grsim_robotstatus.proto
  simulation_config.proto
  simulation_control.proto
  simulation_error.proto
  simulation_robot_control.proto
  simulation_robot_feedback.proto
  simulation_synchronous.proto
  vision_detection.proto
  vision_detection_tracked.proto
  vision_geometry.proto
  vision_wrapper.proto
  vision_wrapper_tracked.proto
)

protobuf_generate(LANGUAGE cpp OUT_VAR generated_files PROTOS ${proto_files})
add_library(ssl-protos-obj OBJECT ${generated_files})
target_link_libraries(ssl-protos-obj protobuf::libprotobuf)
