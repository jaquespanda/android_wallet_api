# Copyright (c) 2014-2015, The Monero Project
#
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without modification, are
# permitted provided that the following conditions are met:
#
# 1. Redistributions of source code must retain the above copyright notice, this list of
#    conditions and the following disclaimer.
#
# 2. Redistributions in binary form must reproduce the above copyright notice, this list
#    of conditions and the following disclaimer in the documentation and/or other
#    materials provided with the distribution.
#
# 3. Neither the name of the copyright holder nor the names of its contributors may be
#    used to endorse or promote products derived from this software without specific
#    prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY
# EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
# MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL
# THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
# SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
# PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
# INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT,
# STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF
# THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

set(cryptonote_core_sources
  account.cpp
  blockchain_storage.cpp
  blockchain.cpp
  checkpoints.cpp
  checkpoints_create.cpp
  cryptonote_basic_impl.cpp
  cryptonote_core.cpp
  cryptonote_format_utils.cpp
  difficulty.cpp
  miner.cpp
  tx_pool.cpp)

set(cryptonote_core_headers)

set(cryptonote_core_private_headers
  account.h
  account_boost_serialization.h
  blockchain_storage.h
  blockchain_storage_boost_serialization.h
  blockchain.h
  checkpoints.h
  checkpoints_create.h
  connection_context.h
  cryptonote_basic.h
  cryptonote_basic_impl.h
  cryptonote_boost_serialization.h
  cryptonote_core.h
  cryptonote_format_utils.h
  cryptonote_stat_info.h
  difficulty.h
  miner.h
  tx_extra.h
  tx_pool.h
  verification_context.h)

bitmonero_private_headers(cryptonote_core
  ${crypto_private_headers})
bitmonero_add_library(cryptonote_core
  ${cryptonote_core_sources}
  ${cryptonote_core_headers}
  ${cryptonote_core_private_headers})
target_link_libraries(cryptonote_core
  LINK_PUBLIC
    common
    crypto
    otshell_utils
    blockchain_db
    ${Boost_DATE_TIME_LIBRARY}
    ${Boost_PROGRAM_OPTIONS_LIBRARY}
    ${Boost_SERIALIZATION_LIBRARY}
  LINK_PRIVATE
    ${Boost_FILESYSTEM_LIBRARY}
    ${Boost_SYSTEM_LIBRARY}
    ${Boost_THREAD_LIBRARY}
    ${EXTRA_LIBRARIES})