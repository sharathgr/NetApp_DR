# Ansible Playbook for Automating NetApp Volume-based Disaster Recovery using REST APIs

## Purpose
This Ansible playbook automates the disaster recovery (DR) process for NetApp volumes using REST APIs. It facilitates failover and failback operations between source and target storage virtual machines (SVMs), ensuring minimal downtime and data integrity during disaster recovery scenarios.

## Playbook Structure

### Failover

- **collect_source_volume_junction_path.yml**
  - Collects the junction path of the source volumes.

- **collect_target_volume_junction_path.yml**
  - Collects the junction path of the target volumes.

- **collect_source_cifs_server_info.yml**
  - Gathers details of the CIFS server on the source SVM.

- **collect_source_cifs_shares.yml**
  - Gathers details of CIFS shares on the source SVM.

- **collect_source_spn.yml**
  - Collects SPN (Service Principal Name) entries for the DNS of the source SVM's CIFS server.

- **stop_source_cifs_create_snapshot.yml**
  - Stops the CIFS server on the source SVM and creates snapshots of all volumes hosted on it.

- **delete_source_cifs_server.yml**
  - Deletes the CIFS server hosts on the source SVM.

- **stop_source_vserver.yml**
  - Stops the source SVM.

- **collect_snapmirror_dr_status.yml**
  - Collects SnapMirror replication status from the target SVM.

- **snapmirror_dr_update.yml**
  - Updates SnapMirror configuration for the target SVM.

- **snapmirror_dr_quiesce.yml**
  - Pauses SnapMirror replication for the target SVM.

- **snapmirror_dr_break.yml**
  - Breaks the SnapMirror relationship for the target SVM.

- **modify_cifs_server_source_to_dr.yml**
  - Copies CIFS server details from the source SVM to the target SVM.

- **modify_cifs_shares_source_to_dr.yml**
  - Copies CIFS shares details from the source SVM to the target SVM.

- **modify_mount_path.yml**
  - Copies volume junction path details from the source SVM to the target SVM.

- **create_dr_cifs_server.yml**
  - Creates a new CIFS server on the target SVM.
    
- **cifs_shares_remove_everyone.yml**
  - Removes Everyone permissions from all CIFS Shares on the target SVM. 

- **mount_target_volumes.yml**
  - Mounts volumes on the target SVM.

- **create_dr_cifs_shares.yml**
  - Creates CIFS shares and updates lm-compatibility-level to ntlmv2-krb on the target SVM.

- **modify_target_volume.yml**
  - Updats snapshot policy, tiering-policy, tiering-minimum-cooloing-days on the target SVM.

- **collect_source_cifs_local_groups.yml**
  - Collects cifs local-groups details from source SVM. 

- **create_source_snapmirror.yml**
  - Sets up SnapMirror to replicate data from the source to the target SVM.

- **collect_snapmirror_source_status.yml**
  - Collects SnapMirror status from the source SVM.

- **resync_source_snapmirror.yml**
  - Resynchronizes data from the target SVM to the source SVM.

### Failback

- **collect_target_cifs_server_info.yml**
  - Collects details of the CIFS server on the target SVM.

- **collect_target_cifs_shares.yml**
  - Collects details of CIFS shares on the target SVM.

- **collect_target_spn.yml**
  - Collects SPN entries for the DNS of the target SVM's CIFS server.

- **stop_target_cifs_create_snapshot.yml**
  - Stops the CIFS server on the target SVM and creates snapshots of all volumes hosted on it.

- **delete_target_cifs_server.yml**
  - Deletes the CIFS server on the target SVM.

- **stop_target_vserver.yml**
  - Stops the target SVM.

- **collect_snapmirror_source_status.yml**
  - Collects SnapMirror status from the source SVM.

- **snapmirror_source_update.yml**
  - Updates SnapMirror configuration on the source SVM.

- **snapmirror_source_quiesce.yml**
  - Pauses SnapMirror replication on the source SVM.

- **snapmirror_source_break.yml**
  - Breaks the SnapMirror relationship on the source SVM.

- **modify_cifs_server_dr_to_source.yml**
  - Copies CIFS server details from the target SVM to the source SVM.

- **modify_cifs_shares_dr_to_source.yml**
  - Copies CIFS shares details from the target SVM to the source SVM.

- **start_source_vserver.yml**
  - Starts the source SVM.

- **create_source_cifs_server.yml**
  - Creates a new CIFS server on the source SVM.

- **create_source_cifs_shares.yml**
  - Creates CIFS shares on the source SVM.

- **collect_snapmirror_target_status.yml**
  - Collects SnapMirror status from the target SVM.

- **resync_target_snapmirror.yml**
  - Resynchronizes data from the source SVM to the target SVM.
